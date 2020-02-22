## Introduction

**_(This page describe future functionality of Pipes, and is currently not available in any Pipes release)_**

This page describe the upcoming native Pipes Compiler to JavaScript. 

The goal of this 'subproject; is achieve high performance code execution, where a Pipes project runs at a (nearly) comparable speed as handcrafted JavaScript.  The goal is to make Pipes ready for high performance production use.

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
- First it tries to find the `dhf/output` block as `finalState`. If it cannot find this block or it finds multiple blocks compilation is aborted. 
- It builds a graph for flow analysis
- It determines all possible paths from s

