# Ethereum development with scaffold-eth

## Setup

```
git clone https://github.com/austintgriffith/scaffold-eth.git smart-contract-sandbox
cd smart-contract-sandbox
```

```
nvm use 10;
yarn install;
```

### Terminal windows

```
#run in original terminal window:
yarn start
#run in terminal window 2:
yarn run chain
#run in terminal window 3:
yarn run deploy
```

### Browser tabs
```
http://localhost:3000/
https://solidity-by-example.org/0.6/
https://solidity.readthedocs.io/en/v0.5.3/units-and-global-variables.html
```

## Create a new contract

Go in `packages/buidler/contracts` and duplicate the default contract. Rename it to your liking.

Open `packages/react-app/src/App.jsx` and find the `<Contract name="..." ... />` component. Change the `name` property to reflect the name of your new contract.

## WETH smart contract

WETH implementation on [github](https://github.com/gnosis/canonical-weth/blob/master/contracts/WETH9.sol) and [etherscan](https://etherscan.io/address/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2#code)

Inspiration:
* [EhterToken.sol](https://github.com/gnosis/util-contracts/blob/master/contracts/EtherToken.sol)
* [VeilEther](https://github.com/veilco/veil-contracts/blob/master/contracts/VeilEther.sol)
