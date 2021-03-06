Subgraphs are here to help you.
If you have a list of documents coming from a source (ex: list of nested objects) or from a search (list of results), you can apply the same processing to all individual items of this list by using a subgraph.

## How to create a subgraph
Go to the menu (right click), and select graph/Subgraph. It will add en empty block to your graph drawing.

## How to edit the subgraph
Just double-click the subgraph block and you will zoom into this subgraph. The whole canvas is now the subgraph drawing.

You can now add input blocks (graph/Input) and output blocks (graph/Outputs) into this subgraph.
The first input you add into the subgraph will represent one item of the list to process, the first output you add will contain all the individual outputs coming from the subgraph.

All the other input(s)/output(s) you add can be anything. Value from these inputs will be provided as is to the subgraph input blocks, and value set in the output blocks will be provided as-is by the outputs of the subgraph block.

You can now design your processing graph by connecting the input(s) with other blocks and to the output(s), as usual.

When you are happy you can close the subgraph, right-click and "Close subgraph".

You can now see you subgraph block is updated with the inputs and outputs you added in your subgraph. The first input and first output have a [Array] label added to their respected names. 
