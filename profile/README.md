
## Inspiration
Liquidity on DEXes is a crucial factor which is responsible for costs of swap (slippages) and liquidity providing efficiency (impernament loss). Low liquidity results in volatility in cryptocurrency prices and exposes the exchanges to market manipulation. Despite the clear benefits of yield farming, DEXes may still struggle to attract liquidity providers to their exchanges. Commonly, DEXes compete for liquidity by offering high annual percentage rates with highly inflationary tokens. However, this obscures the effective APR of staking tokens. We recognise the need for an effective manner to attract liquidity providers. What better way to do so than through game entertainment- a highly commercial activity. Games will make token staking more enticing to users. It would also attract recurrent staking by users due to its addictive nature.

## What it does
Liquidity Wars is a decentralized protocol that addresses the lack of liquidity in DeFi. Our protocol offers DEXes the ability to easily scaffold a no-loss, play and earn, decentralized strategy game which runs autonomously. Players deploy their liquidity to play in the game. At the end of the game each player can redeem the same amount of liquidity tokens (LP). 

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/GameFlow.png" alt="drawing" width="800" height="450"/>

The main rules in the game are to get as many resources (RES) as it is possible. The RES is the in-game unit and will be the base for rewards distributions which will be derived from LP tokens rewards. In order to get RES players can attack and rob each other, develop infrastruture to get more resources, increase defence or places to hide RES from the aggressor. The purpose of the project is to not be another play to earn game but to be play **and** earn game which will atract potential investors to provide and lock their liquidity. 

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/RewardsRatioAndEarnings.png" alt="drawing" width="800" height="450"/>

Main source of protocol income will be RES which is transferred every building upgrade, troops creation and attacks. At the end of the game, smart contract address will be treated similarly as other players and get the rewards from mentioned ratio. Only smal percentage of RES spent in the game will be transfered and the rest will be burnt reducing by this total supply of RES.

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/ProtocolEarning.png" alt="drawing" width="800" height="450"/>

The targets of the projects are not only players but DEXes which will want to increase liquidity by our game. Using our protocol, DEXs will be able to configure which Liquidity Provider (LP) tokens are required for users to deposit in order to join their game. They will have freedom to determine other game configurations such as game duration, deposit amount, player attributes and determine which LP tokens will be assigned to specific nation (orcs, elves, human, dwarfs). What is most important DEXes will be able to determine its own strategies for LP tokens:

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/DesiredGameFlow.png" alt="drawing" width="800" height="450"/>

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/GameConfigAndStrategies.png" alt="drawing" width="800" height="450"/>

## How we built it

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/Architecture.jpg" alt="drawing" width="800" height="450"/>

- The smart contracts behind our protocol are written in Solidity with the help of the Hardhat framework.
- Chainlink VRF is used for bringing randomization into our game's battle system.
- Chainlink Automation is used to automate the starting and ending of the game. It also automates the transfer of the LP tokens back to the players and the awarding of the rewards tokens when the game ends.
- Chainlink Price Feeds are used for the calculation of the price of the LP Tokens in USD. This allow the DEXes to configure the stable value in USD which will be reflected in LP tokens required to participate in their games. 
- Polygon was our choice of blockchain to deploy the smart contracts. This is because it is a Layer 2 protocol that offers cheap gas fees and fast transactions. This allows our game to run smoothly as the players can interact with our contract functions with low amounts of gas fees and short block-confirmation duration.
- Quicknode was used as the RPC node provider for the smart contracts tests due to the high reliability it offers. It is also compatible with both Polygon mainnet and testnet networks for deployment. In the pre-built game interface, quicknode was used for querying smart contract events.
- Our sample frontend interface was mainly built using NextJS React framework. Moralis and Ethers.js were used for the smart contract interactions.

## Challenges we ran into
1. Set up multiple keepers and using checkData and performData to steer the logic dependent on conditions.
2. Get number of required LP tokens to start the game basing on calibrated required USD amount and price feeds.
3. Design smart contracts structure so that they will not exceed maximum smart contract size for deployment.
4. Simulate dummy rewards for the LP pool due to lack rewards of mumbai network.
5. Emit event in such a way that will be able to filter.

## Accomplishments that we're proud of
1. Battle system which using VRF randomized number and some constant factors to calculate outcomes.
2. Working keepers which assure that game autmatically changes states and distributes rewards when game is running.
3. Fully responsive frontend.
4. Logging attacks/defences for each players

## What we learned
1. How to emit and filter events in the front-end.
2. How to design reasonably sized smart contracts without stack too deep erors.

## What's next for Liquidity Wars
- Allow to accept more LP tokens and assign each token to the nations (orc, elves, human, dwarfs). Each nation will have some special bonuses to troops and buildings. Example: dwarfs will be better in defense and orcs will be better in ofense
- Provide fully configurable game and strategies - that allows dexes to configure the game as they wish (game duration, additional rewards, allowed LP tokens). It will be achieved by usage of low-level solidity encoded calldata.
- Introduce tradeable ERC1155 tokens with metadata stored on IPFS which creates some bonuses to the game.
- Introduce special building the root which will provide some bonuses basing on the LP price to corresponding nation.
  
Notice: More specific functionalities which can be done is mentioned [here](../../front-end/TODO.md)
 
