# 🥞 Pancake Frontend fork

<!---
[![Netlify Status](https://api.netlify.com/api/v1/badges/7bebf1a3-be7b-4165-afd1-446256acd5e3/deploy-status)](https://app.netlify.com/sites/pancake-prod/deploys)
-->

This project contains the main features of the pancake application.

If you want to contribute, please refer to the [contributing guidelines](./CONTRIBUTING.md) of this project.

In `/contracts` you can find some of the https://github.com/pancakeswap/pancake-farm contracts (and most of the code).

## Description
This is a fork of [pancakeswap-frontend](https://github.com/pancakeswap/pancake-frontend).
The idea for it is to be ran on the ethereum network. Since pancakeswap was originally a uniswap fork, I believe it should be doable.
I will first try to make it work on one of the eth test networks, and if it works I might deploy it on the [cheapeth network](https://cheapethereum.org/) (which is another ethereum fork).

## To update this repo with the changes from the original pancakeswap-frontend repo:
`git remote update`

## Starting
1) Install dependencies:
`yarn`

2) Start the frontend server:
`yarn start`

* To start it as a development server:
`yarn start --env=development`
* Also don't forget to either export the infura project id:
`export PROJECT_ID="infura project id"`
OR
Copy `.env.development` to `.env.development.local` and change the `REACT_APP_NODE_1` url to include the infura project id

#### Node Modules:
Copy the pancakeswap-sdk and pancakeswap-uikit folders inside SDK-UIKIT folder and paste them in the node modules folder in omnidex-exchange-frontend
