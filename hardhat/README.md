# Hardhat!

This guide helps with all the environment setup for Web3 development. 


## Setup 


- Create new directory
```console
mkdir hardhat-fund-me-fcc
```
- Go inside the directory
```console
cd hardhat-fund-me-fcc
```
- Open that directory on VSCode
- Initialize  **yarn**
```console
yarn init
```
- Add **hardhat** using **yarn**
```console
yarn add --dev hardhat
```
- Run **hardhat** and choose `Create a JavaScript project`
```console
yarn harhat
```
- Add **prettier**
```console
yarn add --dev prettier prettier-plugin-solidity
```
- Add prettier rc file `.prettierrc` on root project
```json
{
	"tabWidth": 4,
	"useTabs": false,
	"semi": false,
	"singleQuote": false
}
```
- Add  `.prettierrc` on `.gitignore` file
- Add prettier ignore file `.prettierignore` on root project
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
- Update Solidity Compiler version on  `hardhat.config.js` 
- Add **chainlink**
```console
yarn add --dev @chainlink/contracts
```

## Compile 

- Compile the contract using:
```console
yarn hardhat compile
```

## Deploy 
Deploy the contract using **hardhat-deploy** plugin

- Install **hardhat-deploy** plugin:
```console
yarn add --dev hardhat-deploy
```
- Add the following statement on `hardhat-config.js`:
```javascript
require('hardhat-deploy');
```
- Delete `scripts/deploy.js` file
- Create new folder `/deploy` inside root
```console
mkdir deploy
```
- Install **hardhat-deploy-ethers** plugin:
```console
yarn add --dev @nomiclabs/hardhat-ethers@npm:hardhat-deploy-ethers ethers
```
- Add `deploy/01-deploy-fund-me.js` file:
```javascript
function  deployFunc(){
	console.log("Hi!");
}
module exports.default = deployFunc
```
- Deploy the contract using:
```console
yarn hardhat deploy
```
