## Introduction

**_(This page describe future functionality of Pipes, and is currently not available in any Pipes release)_**

This page describe the upcoming native Pipes Compiler to JavaScript. 

The goal of this 'subproject' is achieve high performance code execution, where a Pipes project runs at a (nearly) comparable speed as handcrafted JavaScript.  The goal is to make Pipes ready for high performance production use.

## How it works

The 'Export DHF Custom Module' will get an option to generate native Javascript. If you graph supports native code generation, a checkbox will be enabled which allow the business developer to select JS code generation. If the graph does not support native code generation, the checkbox is disabled (grayed out).  See in a next section what supports native code generation and what not. 

## Which graphs can be compiled to native JavaScript?

Graphs can be compiled to native JavaScript only if the graph:

- Has only 1 DHF Input node. E.g. an empty graph cannot be compiled.
- Has only 1 DHF output node.
- Has a path from DHF Input to DHF output node (the input and output node are (in)directly connected. E.g. a new Pipes graph with only a DHF Input node, and output node without connection cannot be compiled. 
- All nodes in all paths from Input to Output have implemented a code generation hook (see below). If all nodes have a code generation function, but only 1 node has not, Javascript cannot be generated.  The first beta will have support for code generation for some built in blocks. 
- Subgraphs are currently in beta 1 not supported
- The graph has no cycle, that is: the output of Node A is used in node B and the output of node B is used in Node A again. 

## How it works under the hood

The `vppBackendService` POST service will get an extra `action` called `compileToJavaScript`. The request body will contain the JSON graph. 

We need to compile server side, because their we can have access to user defined blocks in `user.sjs`.

This service returns a JSON in the form of: 

```
{ sourceCode = "generated multiline JavaScript code.",
  errors : [ { errorCode : "ERROR_CODE"
               errorDescription : "ErrorDescription" } 
              ...
           ]
}
``` 
Typically if there are errors, `sourceCode` will be empty, and `errors` will be filled, and vice-versa. This allows the Pipes client to display the errors. 

## The compilation process

The compilation process is executed as follows:

- First it tries to find the `dhf/input` block as `startState`. If it cannot find this block or it finds multiple blocks compilation is aborted. 
- Then it tries to find the `dhf/output` block as `finalState`. If it cannot find this block or it finds multiple blocks compilation is aborted. 
- It builds a graph for flow analysis
- It determines all possible paths from `startState` to `finalState`.
- It removes all dead nodes. That are nodes which are unreachable from `startState` to `finalState`
- It checks that there is no cycle in the remaining graph. If there is a cycle, compilation is aborted. 
- It checks that all blocks support code generation (see below). If one of the blocks does not support code generation, compilation is aborted. 
- Based on the flow graph and paths, it determines in which order the blocks need to be executed. 
- Based on this order, it generates code for each block. 

## Code generation support for blocks

Every block which supports code generation should implement the following function:

```
<name>.prototype.onCodeGeneration = function(tempVarPrefix,inputVariables,outputVariables,propertiesWidgets)
```

Here:

- The return value is an array of strings with generated code. 
- `tempVarPrefix` is a string which this block need to use as prefix if it generates variables. This ensure the variables within the block are unique.
- `inputVariables` are the names of the variables to use as input, in the form of:

```
{ input0 : "variableName",
  input1 : "variableName2",
  ...
}
```
  - So, the alternative for `this.getInputData(0)` is `inputVariables.input0`. For this construction is chosen so that during code generation you can easily check a input is connnected via `"input0" in inputVariables` which will be `false` if input 0 is not connected. 

  - The alternative for `this.setOutputData(0)` is `outputVariable.output0`

- `propertiesWidgets` will contain the value of the properties and widgets in the form of: 

```
{ properties: { widgetKey: "widgetValue", widgetKey2: widgetValue,... },
   widgets: { propertyKey: "propertyValue", propertyKey2: "propertyValue2",....}
```
## Example code generation function

Here is an example:

```
  stringTemplate.prototype.onCodeGeneration = function(tempVarPrefix,inputVariables,outputVariables,propertiesWidgets) {
    let code = [];
    let template = propertiesWidgets.widgets.template;
    if ( "input0" in inputVariables ) {
      template = template.replace("v1", inputVariables.input0);
    }
    if ( "input1" in inputVariables ) {
      template = template.replace("v2", inputVariables.input1);
    }
    if ("input2" in  inputVariables ) {
      template = template.replace("v3", inputVariables.input2);
    }
    if ( "v4" in propertiesWidgets ) {
      code.push("let "+tempVarPrefix+"v4="+propertiesWidgets.v4+";");
      template = template.replace("v4", tempVarPrefix + "v4")
    }
    if ( "v5" in propertiesWidgets ) {
      code.push("let "+tempVarPrefix+"v5="+propertiesWidgets.v5+";");
      template = template.replace("v4", tempVarPrefix + "v5")
    }
    code.push("let "+outputVariables.output0+" = eval(`"+template+"`);");
    return code;
  };
```

This will produce in our example:

```
// Start code for string/Templating - nodeId = 14
let var_14_0_newString = eval(`/final/DAMO/${var_17_0_rowNr}.json`);
```

And this:

```
 xpathBlock.prototype.onCodeGeneration = function(tempVarPrefix,inputVariables,outputVariables,propertiesWidgets) {
    let code = [];
    let namespaces = propertiesWidgets.widgets.namespaces;
    let ns = {};
    if ( namespaces && namespaces.trim().length > 0 ) {
      const nstokens = namepaces.trim().split(",");
      if ( nstokens.length % 2 === 0 ) {
        for ( let i = 0 ; i < nstokens.length ; i+=2 ) {
          ns[nstokens[i].trim()] = nstokens[i+1].trim();
        }
      }
    }
    let nsString = JSON.stringify(ns);
    code.push("let "+outputVariables.output0+" = "+inputVariables.input0+"[0].xpath('"+propertiesWidgets.widgets.xpath+"',"+nsString+");");
    return code;
  };
```

Will produce:

```
// Start code for transform/xpath - nodeId = 6
let var_6_0_nodes = var_5_0_instancefeatureMember[0].xpath('fn:name()',{});
```