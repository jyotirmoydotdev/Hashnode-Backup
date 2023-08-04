---
title: "How to interact with Smart Contract?"
datePublished: Tue Mar 21 2023 20:41:51 GMT+0000 (Coordinated Universal Time)
cuid: clfiq1hmp000109l1fc9vc246
slug: how-to-interact-with-smart-contract
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691137199255/7eeeb2cf-6c23-405b-915a-651bc5a1b890.jpeg
tags: tutorial, blockchain, ethereum, smart-contracts, ethers

---

This article will teach you how to interact with a smart contract in the Ethereum blockchain, starting this article we first need to install some dependencies in our computer.

* Node.js - [Click Here](https://nodejs.org)
    
* Ethers.js - [Click Here](https://docs.ethers.org/v5/getting-started/)
    
* Infura ID - [Click Here](https://www.infura.io)
    

After we have installed these dependencies, let's get started with the code. There are many smart contracts in the Ethereum blockchain, a **Token** is also a smart contract for now, we are going to use the Dai Stablecoin ([view in Ethersan](https://etherscan.io/token/0x6b175474e89094c44da98b954eedeac495271d0f)) smart contract to interact with it.

We will use the DAI Smart contract to check someone's DAI token balance in their account and fetch the name, symbol, and total supply of Dai tokens.

## Import ethers.js

Make a folder `Learn-ethers` and create a javascript file `Intreact-with-Smart-contarct.js` open the file in our desired code editor for now we are using vs code.

```javascript
const {ethers}=require ("ethers");
```

## Set the provider

After you created an Infura account create a project, select web3 and give a name to your project. Now you will get an API key, and copy the Ethereum Endpoint.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679420896789/3cefd7ff-3680-408a-9f31-a385d3ee7b8b.jpeg align="center")

Create a const variable `provider` and use the `ethers.providers.JsonRpcProvider(' ')` function to set the provider, with the providers we can interact with the Ethereum blockchain.

```javascript
const {ethers}=require ("ethers");

// Replace the Endpoint with your coped Endpoint
const provider=new ethers.providers.JsonRpcProvider(/*EndPoint*/);
```

## Import the Contract ABI

As we know, we have a function in solidity inside a contract function, and before we can deploy the file to the network we need to compile the code, after compilation the code turns into a JSON object which we call ABI ( ***Application Binary Interface*** ), so to interact with DAI smart contract we need its ABI but where we can get it? We can obtain it from [Ethersan](https://etherscan.io). To find the DAI smart contract just type `DAI stable coin etherscan` in google, you probably get in the first link or you just [click here](https://etherscan.io/token/0x6b175474e89094c44da98b954eedeac495271d0f#code).

Scroll down until you see **Contract ABI,** There you will see a bunch of nonsense code but it is just compiled solidity code, copy the whole code and can save it inside a javascript file `DAI.js` remember Ethereum Request for Comment 20 (ERC-20) is **the implemented standard for fungible tokens created using the Ethereum blockchain.**

Create a file `Dai.js` inside it creates a variable `const Dai=` after it pastes the ABI code and exports the code with the `module.exports={Dai}` this will help us to use this JSON object from our main `Intreact-with-Smart-contarct.js` file.

```javascript
const Dai= /* Paste the ABI code here */
module.exports={Dai}
```

Head over to our main file `Intreact-with-Smart-contarct.js` and import the ABI so we can use it here. and save it into a `ERC20_ABI` variable.

```javascript
const {ethers}=require ("ethers")
const {Dai}=require("./Dai.js")

// Replace the Endpoint with your coped Endpoint
const provider=new ethers.providers.JsonRpcProvider(/*EndPoint*/);

const ERC20_ABI=Dai;
```

## Connecting with Contract

So till now, we got our Contract ABI and provider but to use the contract we need the contract address, which we can get from Etherscan. DAI contract address is `0x6B175474E89094C44Da98b954EedeAC495271d0F` save it into a variable `ContractAddress`.

```javascript
const {ethers}=require ("ethers")
const {Dai}=require("./Dai.js")

// Replace the Endpoint with your coped Endpoint
const provider=new ethers.providers.JsonRpcProvider(/*Endpoint*/);
const ERC20_ABI=Dai;

const ContractAddress= '0x6B175474E89094C44Da98b954EedeAC495271d0F';
```

We got everything to connect with the DAI smart contract, ethers have a function with which we can interact with the smart contract `ethers.Contract(address, ERC20_ABI, provider)` which takes the contract address, contract ABI, and the provider. We will create a variable `contract` in which we will use this function.

```javascript
const {ethers}=require ("ethers")
const {Dai}=require("./Dai.js")

// Replace the Endpoint with your coped Endpoint
const provider=new ethers.providers.JsonRpcProvider(/*EndPoint*/);
const ERC20_ABI=Dai;
const contractAddress= '0x6B175474E89094C44Da98b954EedeAC495271d0F';

const contract= new ethers.Contract(contractAddress, ERC20_ABI, provider);
```

## Fetching the DAI balance of an account

As javascript is an asynchronous language line does not execute line by line, so we need to use an async function in which we can use the keyword `await` which will help us to wait for the code to fetch the Dai balance from the network (the Ethereum blockchain is slow).

DAI smart contract has a function `balanceOf( address )` that takes an account address and returns a unit. The balance will be stored in 27 digits numbers which will be a very big number, we need to use the `ethers.utils.formatEther()` function to view it in DAI.

```javascript
const {ethers}=require ("ethers")
const {Dai}=require("./Dai.js")

// Replace the Endpoint with your coped Endpoint
const provider=new ethers.providers.JsonRpcProvider(/*EndPoint*/);
const ERC20_ABI=Dai;
const contractAddress= '0x6B175474E89094C44Da98b954EedeAC495271d0F';
const contract= new ethers.Contract(contractAddress, ERC20_ABI, provider);

const main=async()=>{
    const balance=await contract.balanceOf(
         "0x25B313158Ce11080524DcA0fD01141EeD5f94b81"
    );
    console.log("Balance: " + ethers.utils.formatEther(balance) + "DAI");
}
main()
```

Run the Javascript file with `node Intreact-with-Smart-contarct.js`.

```bash
Blance: 104818599.30661396439663861 DAI
```

## Fetch the Token Details

DAI smart contract has also some functions with which we can fetch the token details like.

* `name()` to get the name of the token
    
* `symbol()` to get the symbol of the token
    
* `totalSupply()` to get the total supply of token
    

```javascript
const {ethers}=require ("ethers")
const {Dai}=require("./Dai.js")

// Replace the Endpoint with your coped Endpoint
const provider=new ethers.providers.JsonRpcProvider(/*EndPoint*/);
const ERC20_ABI=Dai;
const contractAddress= '0x6B175474E89094C44Da98b954EedeAC495271d0F';
const contract= new ethers.Contract(contractAddress, ERC20_ABI, provider);

const main=async()=>{
    // Fethcing the balance
    const balance=await contract.balanceOf(
         "0x25B313158Ce11080524DcA0fD01141EeD5f94b81"
    );
    console.log("Balance: " + ethers.utils.formatEther(balance) +
    "DAI");
    
    // Fetching the Token Details
    const TokenName=await contract.name();
    const TokenSymbol=await contract.symbol();
    const TokenTotalSupply=await contract.totalSupply();

    console.log("Token Name: " + TokenName);
    console.log("Tokens Symbol: " + TokensSymbol);
    console.log(
        "Token Total Supply: " + 
        ethers.utils.formatEther(TokenTotalSupply) +
        "DAI"
    );
}
main()
```

```bash
Balance: 104818599.30661396439663861 DAI
Token Name: Dai Stablecoin
Token Symbol: DAI
Token Total Supply: T5386818093.718042652998265691 DAI
```