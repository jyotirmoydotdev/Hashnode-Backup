---
title: "Fetch Balance from Ethereum Blockchain"
datePublished: Fri Mar 17 2023 10:25:55 GMT+0000 (Coordinated Universal Time)
cuid: clfce9ze0001b09jt3jqhaxyd
slug: fetch-balance-from-ethereum-blockchain
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679047679017/56a244cf-1a3c-4a90-bcc7-c5057fd8e4e3.jpeg
tags: ethereum, ethers

---

To Fetch the balance of an account in the Ethereum blockchain first we need to install some dependencies on our computer.

* Node.js \[To install the node [`click here↗️`](https://nodejs.org/en)\]
    
* Ethers.js \[Ethers.js Docs [`click here↗️`](https://docs.ethers.org/v5/getting-started/)\]
    

## Import Ethers.js

First, create a folder, let's name it `Learn-ethers`, you can make a folder with the command `mkdir Learn-ethers` after that navigate to the folder `cd Learn-ethers`.

Type the below command in your folder, this will install the Ethers.js in your folder.

```bash
npm install ethers
```

After your successfully installed ethers create a file, you can make a file in the terminal with the command `touch main.js`. Open the file in VS Code or Vim.

We just need to write one line to import ethers in our file.

```javascript
const { ethers } = require("ethers");
```

## Connect with a Node Provider

To interact with a blockchain we need a node that can read, create, or do a transition in the blockchain. We can set up our node but it is not recommended as it will take a lot of time and resources Instead, we can use a node provider such as **Infura**, **Alchemy,** and **Ankr**.

For our tutorial, we can use **INFURA** which provides a node for our tutorial. Let us first create an account in Infura, and head over to [infura.io](https://www.infura.io) and create an account. After you create an account, we need an API key which we will use to interact with the blockchain. Click on <mark>CREATE NEW API KEY </mark> and select Network to Web3 API and give a project name `Learn-ethers`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679031161330/1b2e690b-5ddd-45cc-9e81-235c156527e4.png align="center")

We created a project and got our API Key, Click on `Learn-ethers.`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679033372900/dbcd7947-59fc-4a0b-8bbd-9739f808f41c.png align="center")

You can find your Endpoint in the Endpoint section, copy the link which looks like `https://mainnet.infura.io/v3/{API Key}`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679034216806/2f751ab3-186b-417b-9e2f-eab698dcef84.jpeg align="center")

Create a variable `provider` and use `ethers.providers.JsonRpcProvider(``)` make sure you are using ` `` ` (Backtick) not this `''` (Apostrophe) if your use Apostrophes you will get an error. Paste the copied link in the function parameter.

```javascript
const { ethers } = require("ethers");

const provider = new ethers.providers.JsonRpcProvider(`Paste the Endpoint here`)
```

## Get an account address to fetch the balance

To fetch the balance of an account we need the account address or public key, you can use your Ethereum main net account address or copy some other account address from [etherscan.io](https://etherscan.io), we can use 0x73BCEb1Cd57C711feaC4224D062b0F6ff338501e this account address for our tutorial. Create a variable `address` in which we will store our account address.

```javascript
const { ethers } = require("ethers");

const provider = new ethers.providers.JsonRpcProvider(`Paste the Endpoint here`)

const address = '0x73BCEb1Cd57C711feaC4224D062b0F6ff338501e'
```

## Fetch balance

Ethers has a function with which we can fetch the balance of any address `provider.getBalance()`, we just need to pass the address which we have stored in the `address` variable and store the balance in a `balance` variable.

```javascript
const { ethers } = require("ethers");

const provider = new ethers.providers.JsonRpcProvider(`Paste the Endpoint here`)

const address = '0x73BCEb1Cd57C711feaC4224D062b0F6ff338501e'

const balance = provider.getBalance(address)
```

## Print the Balance in the console

JavaScript is an asynchronous programming language which means it does not wait for a line to complete and move on to the next line, we can use `console.log(balance)` but as the blockchain is slow it may not fetch the balance, you may see something like `Promise {<pending>}` instead, we can use the keyword `await` to wait for the balance to be fetched and then print the balance on the screen.

```javascript
 const balance = await provider.getBalance(address)
```

But to use this keyword we need to write this line in an `async` function, let's make an async function and store it in the main variable and call the main function at last.

To display the balance in ETH we need to do some formatting, we can use the `ethers.utils.formatEther(balance)` function.

```javascript
const main = async () => {
    const balance = await provider.getBalance(address)
    console.log(`\nETH Balance of ${address} --> ${ethers.utils.formatEther(balance)} ETH\n`)
}
main()
```

You can check the balance in [etherscan.io↗️](https://etherscan.io/address/0x73BCEb1Cd57C711feaC4224D062b0F6ff338501e) to confirm that your code is running correctly.

## Full Code

Run this code with `node main.js`

```javascript
const { ethers } = require("ethers");

const provider = new ethers.providers.JsonRpcProvider(`Paste the Endpoint here`)

const address = '0x73BCEb1Cd57C711feaC4224D062b0F6ff338501e'

const main = async () => {
    const balance = await provider.getBalance(address)
    console.log(`\nETH Balance of ${address} --> ${ethers.utils.formatEther(balance)} ETH\n`)
}

main()
```

%%[links]