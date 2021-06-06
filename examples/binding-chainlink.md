# Binding ChainLink Price Feed SmartContract

## Introduction

!> To be able to start the tutorial you need to have done the **Log in the Terminal** tutorial, we will assume that you have done it before

In this tutorial we will bind a **ChainLink Price Feed SmartContract** from the **Ethereum Blockchain** and export each values in your graph.

## Setup the JSON ABI

For querying any SmartContract we need a **JSON ABI** of the contract itself.  
You will get it **from Etherscan directly if the contract is verified**.  

For the ChainLink Price Feed, we will take the **BTC/USD** price feed.  
[Link to the Etherscan contract](https://etherscan.io/address/0xF4030086522a5bEEa4988F8cA5B36dbC97BeE88c)  
In the **Contract** section we can retrieve the ABI for the contract, copy it and fill the **JSON ABI** block with the ABI copied.

<img src="https://i.imgur.com/CbsNusA.png" style="border-radius: 10px; margin: 20px;"/>

## Lua Script

In the **JSON ABI** you have all the method that you can query.  
The method that we need, is the **latestRoundData** method to request the latest price available on the contract.

To call the method we will use the Lua method **CallContractFunction(methodName, inputParameters)** from the GraphLinq Lua Engine.  
The method will return you a array with all result parameters in it.

We will bind all the results in variables in the Lua Script to be able to export them to the Graph.

!> Lua array index start at the index **1**

```lua
-- Fetch data from Chainlink Price Feed
roundData = CallContractFunction("latestRoundData", {})
roundId = roundData[1]
answer = roundData[2]
startedAt = roundData[3]
updatedAt = roundData[4]
answeredInRound = roundData[5]
```

Now we have the variables ready to be exported, we will use the method **ExportParameter(name, value)** to export them.  

To export the **answer** parameter we will convert it do double with the decimals count given in the smart contract.  
So for USD we need to convert the **BigInteger to double value with 8 decimals**.  
We will use the method **CastBigIntegerToDouble(value, decimal)** to cast it.

```lua
-- Export parameters to the graph
ExportParameter("roundId", roundId)
ExportParameter("answer", CastBigIntegerToDouble(answer, 8))
ExportParameter("startedAt", startedAt)
ExportParameter("updatedAt", updatedAt)
ExportParameter("answeredInRound", answeredInRound)
```

### Complete Lua Script

```lua
-- Fetch data from Chainlink Price Feed
roundData = CallContractFunction("latestRoundData", {})
roundId = roundData[1]
answer = roundData[2]
startedAt = roundData[3]
updatedAt = roundData[4]
answeredInRound = roundData[5]

-- Export parameters to the graph
ExportParameter("roundId", roundId)
ExportParameter("answer", CastBigIntegerToDouble(answer, 8))
ExportParameter("startedAt", startedAt)
ExportParameter("updatedAt", updatedAt)
ExportParameter("answeredInRound", answeredInRound)
```

## Parameters Linking

> Now you need to have a graph like this  

<img src="https://i.imgur.com/3OM0EvW.png" style="border-radius: 10px; margin: 20px;"/>

## Print the output value from the Lua Script

**Now that we have fetched values from the Price Feed Smart Contract** we can use them as we want in our graph.  
We will use a basic **Print** block to output it in the **IDE Terminal**.  

To retrieve output parameters from the Lua Context, we will use the **Get Lua Exported Parameter** block and get the **answer** value
<img src="https://i.imgur.com/XS1IOAH.png" style="border-radius: 10px; margin: 20px;"/>

## Run the graph

To run the graph, just press **CTRL+E** or execution it with the **Execution Menu**.  
After few seconds, you will see in your IDE terminal the output of the graph with the **answer value from ChainLink Price Feed** from the Lua Script.
<img src="https://i.imgur.com/U4LhFpX.png" style="border-radius: 10px; margin: 20px;"/>

