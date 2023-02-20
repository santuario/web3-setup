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

# Hardhat


## Setup 


- Create new directory
```console
mkdir hardhat-simple-storage
```
- Go inside the directory
```console
cd hardhat-simple-storage
```
- Init *yarn* project

```console
yarn init 
```
- Add *Hardhat* functions

```console
yarn add --dev hardhat 
```

- Run *Hardhat*

```console
yarn hardhat 
```
or
```console
npx hardhat 
```
- Select **Create a Javascript project**

## Config 


- Add prettier
```console
yarn add --dev prettier prettier-plugin-solidity
```
- Add prettier rc file *.prettierrc* on root project
```json
{
	"tabWidth": 4,
	"useTabs": false,
	"semi": false,
	"singleQuote": false
}
```
- Add prettier ignore file *.prettierignore* on root project
```console
node_modules
package.json
img
artifacts
cache
coverage
.env
.*
README.md
coverage.json
```
- Add *dotenv*
```console
yarn add --dev dotenv
```
- Create *.env*  on root project
```console
GOERLI_RPC_URL=
PRIVATE_KEY=
ETHERSCAN_API_KEY=
COINMARKETCAP_API_KEY=
```

- Edit *hardhat.config.js*
```javascript
require("@nomicfoundation/hardhat-toolbox");
require("dotenv").config();

/** @type import('hardhat/config').HardhatUserConfig */

const  GOERLI_RPC_URL = process.env.GOERLI_RPC_URL;
const  PRIVATE_KEY = process.env.PRIVATE_KEY;

module.exports = {
defaultNetwork:  "hardhat",
networks: {
goerli: {
url:  GOERLI_RPC_URL,
accounts: [PRIVATE_KEY],
chainId:  5,
},
},
solidity:  "0.8.8",
};
```
- Add *etherscan verify*
```console
yarn add --dev @nomiclabs/hardhat-etherscan
```
And add the following statement to your `hardhat.config.js`:
```js
require("@nomiclabs/hardhat-etherscan");
```
And, in the same file, add:
```js
etherscan: {
	apiKey:  ETHERSCAN_API_KEY,
},
```
Go to *etherscan* to get the **API KEY**

- Add *gas reporter*
```console
yarn add --dev hardhat-gas-reporter
```
And add the following statement to your `hardhat.config.js`:
```js
require("hardhat-gas-reporter");
```
And, in the same file, add:
```js
gasReporter: {
	enabled:  true,
	outputFile:  "gas-report.txt",
	noColors:  true,
	currency:  "USD",
	coinmarketcap:  COINMARKETCAP_API_KEY,
},
```
Go to *coinmarketcap* to get the **API KEY** and add `gas-report.txt` in `.gitignore` file

- Add *solidity coverage*
```console
yarn add --dev solidity-coverage
```
And add the following statement to your `hardhat.config.js`:
```js
require("solidity-coverage");
```
Add `coverage.json` file and `coverage` folder in `.gitignore` file

## Deploy Contract 

- Run on default network
```console
yarn hardhat run scripts/deploy.js
```
- Run on goerli network
```console
yarn hardhat run scripts/deploy.js --network goerli
```

## Deploy Contract Locally

- If you'd like to run your own local hardhat network, you can run:
```console
yarn hardhat node
```
And add the following statement to your `hardhat.config.js` inside `networks`:
```js
localhost: {
	url:  "http://127.0.0.1:8545/",
	chainId: 31337,
},
```
- And then **in a different terminal**
```console
yarn hardhat run scripts/deploy.js --network localhost
```
## Clean compiled contracts

- Clean `artifacts` and `cache` folder:
```console
yarn hardhat clean
```
## Testing contracts

- Check that inside `test` directory exists one file `<>.js` and run:
```console
yarn hardhat test
```

## Coverage Contract 

In order to see how many percentage of the code is included on testing asserts:

- Run 
```console
yarn hardhat coverage
```
