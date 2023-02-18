# Welcome to Web3 Setup!

This guide helps with all the environment setup for Web3 development. 

# Tools

Install the following tools needed for development.

## Installation & Setup

 - [Visual Studio Code](https://code.visualstudio.com/)
 - [Solidity VSCode Extension](https://marketplace.visualstudio.com/items?itemName=NomicFoundation.hardhat-solidity)
 - [Node.js](https://nodejs.org/en/)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) 
- Format Solidity VSCode with ( View > Command Palette: Open Settings JSON):

```
    "[solidity]": {
        "editor.defaultFormatter": "NomicFoundation.hardhat-solidity"
    },
    "[javascript]":{
      "editor.defaultFormatter": "esbenp.prettier-vscode"
    }
```
- Install **yarn**:
```
corepack enable
```
```
yarn --version
```
- [Ganache](https://trufflesuite.com/ganache/)


# Template


## Setup Local Environment Development

```console
mkdir ethers-simple-storage
```
Add Solidity Compiler:
```
yarn add solc
```
For the current solidity:
```
yarn add solc@0.8.7-fixed
```
Try from command line:
```
yarn solcjs --bin --abi --include-path node_modules/ --base-pa
th . -o . SimpleStorage.sol 
```
Add Ethers.js:
```
yarn add ethers@5.4
```
Add Env:
```
yarn add dotenv
```

For password:
```
PRIVATE_KEY_PASS=miauguau node deployv2.js
```
