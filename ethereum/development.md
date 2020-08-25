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
