# GraphLinq Lua Scripting Documentation

> GraphLinq support Lua to write custom blocks for your graph on the platform

This documentation allow you you to understand how to use Lua for your custom blocks.  
Each functions will be detailled with some use cases and how to use them in your script.

> The supported Lua version is Lua 5.2 at 99% (with the only unsupported feature being weak tables support)

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Lua-Logo.svg/1200px-Lua-Logo.svg.png" width="200" style="margin: 20px"/>
<img src="https://media-exp1.licdn.com/dms/image/C4E1BAQHC17rsaE2bbA/company-background_10000/0/1618411267786?e=2159024400&v=beta&t=tZ97dZ2-H69fHVzruB8M6VXfCQ2iNSbljnupS_JG5vc" width="420" style="border-radius: 10px; margin: 20px;"/>

## Features
- Easy custom SmartContract integration directly in Lua
- Support for metalua style anonymous functions (lambda-style)
- An embedded JSON parser (with no dependencies) to convert between JSON and Lua tables
- Script run in a sandbox
- Custom interaction with your graph from Lua (call functions, emit events ..)
- Script error directly on your GraphLinq dashboard or in terminal logs