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

(In order of how I got everything setup step by step)

Download frontend, toolkit, and sdk then extract all 3 in the same folder.
Launch my router, factory, cake token, Masterchef, Syrup contracts without any changes. Then verify each contract.
3 Install each project (frontend, toolkit, & sdk) using "yarn install".
Change factory address and INIT_CODE_HASH in (sdk root>src>constants) then build the project with "yarn build".
Copy the dist file created in the root folder into the front end folder (front end> node_modules>@pancakeswap>sdk) .
Now we have a working trading system that runs on my own factory and router. You can do anything at this point from trading to selling and adding liquidity to tokens.

Steps to reproduce crash on farming:

Make sure all values and addresses punched into the contracts are set correctly.
Change masterchef contract address from "Panckeswaps" to ours. (front end>src>config>constants>contracts.ts)
Reload home page.
As page reloads everything looks normal until the profile located at the top starts to load then we are presented with a crash.
Expectations
I had assumed changing this value alone would be enough to redirect values to my Masterchef contract. If anyone can assist me with figuring this out that would be awesome.

Note: I did add the liquidity tokens into the masterchef "add" function to see if this would resolve the issue. Normally I would not be able to add anything to a farm without getting the error "Do you add enough gas?" but that is after I hit "activate farm" then "Stake".

Update:

I managed to get everything up and running! What I was missing was the hooks.ts file. Within it you can find pid 251 and 252. Changing these to match both my cake-busd and bnb-busd as well as changing the cake token address within tokens.ts managed to fix all of my issues. Tho some of my tokens will not display their APR 3 will however.
