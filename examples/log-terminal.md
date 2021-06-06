# Log in the Terminal

## Introduction

> We will start with the most basic feature of the GraphLinq Scripting Engine : **Logging**  

It will allow you the log any kind of text on your GraphLinq Dashboard or in your IDE Terminal.  
This is usefull to debug your script or just log some informations to track things.

## Lua Script

To be able to execute a Lua Script we will add a **Lua Script** block in our Graph.

<img src="https://i.imgur.com/ALBEmla.png" style="border-radius: 10px; margin: 20px;"/>

To write log we will use the function **Log(message)** in our Script
```lua
Log("Hello from GraphLinq Lua !")
```

## Parameters Linking

To create Lua execution context we will use the **Ethereum Smart Contract Lua Function** block.  
We need to fill some parameters to be able to run the script even if we don't query any smart contract yet.  

- For the Ethereum Connector, just link a **Ethereum Connector** node.
- For the Contract Address, link a **String** block and with the value **0x0**
- For the Lua Parameter, link the **Lua Script** block
- For the JSON ABI, since we doesnt link a smart contract yet just add a block **JSON ABI** and fill it with the value **[]**
- You don't need to link any **InputParameters** for now

For the execution flow, add a block **On Graph Start** and link it to the execution parameter

<img src="https://i.imgur.com/5QBUo7A.png" style="border-radius: 10px; margin: 20px;" />

## Run the graph

To run the graph, just press **CTRL+E** or execution it with the **Execution Menu**.  
After few seconds, you will see in your IDE terminal the output of the graph with **Log** from the Lua Script.

<img src="https://i.imgur.com/kuCa2QP.png" style="border-radius: 10px; margin: 20px;" />