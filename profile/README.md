
## Inspiration
Liquidity on DEXes is a crucial factor which is responsible for costs of swap (slippages) and liquidity providing efficiency (impernament loss). Low liquidity results in volatility in cryptocurrency prices and exposes the exchanges to market manipulation. Despite the clear benefits of yield farming, DEXes may still struggle to attract liquidity providers to their exchanges. Commonly, DEXes compete for liquidity by offering high annual percentage rates with highly inflationary tokens. However, this obscures the effective APR of staking tokens. We recognise the need for an effective manner to attract liquidity providers. What better way to do so than by bringing the concept of play **and** earn to the DEX market. We see it as a highly-attractive commercial tool for bringing new liquidity providers to the scene. We believe games can make tokens staking more enticing to users. It would also attract recurrent staking by users due to its addictive nature.

## What it does
Liquidity Wars is a decentralized protocol that addresses the lack of liquidity in DeFi. Our protocol offers DEXes the ability to easily scaffold a no-loss, play and earn, decentralized strategy game which runs autonomously. Players deploy their liquidity to play in the game. At the end of the game each player can redeem the same amount of liquidity tokens (LP). 

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/GameFlow.png" alt="drawing" width="800" height="450"/>

The main objective of the game is to get as many resources (RES) as possible. The RES is the virtual in-game currency that will be the base for the calculation of the rewards distributions. Those rewards will be derived from the LP tokens rewards. In order to get RES players can attack and rob each other, develop infrastruture to get more resources, increase defense or build protection to hide RES from the attacker. The purpose of the project is not to be another play to earn game but to be play **and** earn game which will atract potential investors to provide and lock their liquidity. 

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/RewardsRatioAndEarnings.png" alt="drawing" width="800" height="450"/>

Main source of protocol income will be rewards calculated basing on RES which is transferred to the contract every building upgrade, troops creation and attacks. At the end of the game, smart contract address will be treated similarly as other players and get the rewards from mentioned ratio. Only small percentage of RES spent in the game will be transfered to the contract and the rest will be burnt reducing by this total supply of RES.

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/ProtocolEarning.png" alt="drawing" width="800" height="450"/>

The target audiences of this project are not only players but DEXes which will want to increase liquidity by implementing our game. Using our protocol, DEXes will be able to configure which Liquidity Provider (LP) tokens are required for users to deposit in order to join their game, as well as several other configurations such as: game duration, deposit amount, player attributes and determine which LP tokens will be assigned to each nation (orcs, elves, human, dwarfs). Mainly DEXes will be able to determine its own strategies for LP tokens:

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/DesiredGameFlow.png" alt="drawing" width="800" height="450"/>

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/GameConfigAndStrategies.png" alt="drawing" width="800" height="450"/>

## How we built it

<img src="https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/Architecture.jpg" alt="drawing" width="600" height="900"/>

- The smart contracts behind our protocol are written in Solidity with the help of the Hardhat framework, Openzeppelin and Chainlink sample contracts.
- Chainlink VRF is used for bringing randomization into our game's battle system.
- Chainlink Automation is used to automate the starting and ending of the game. It also automates the transfer of the LP tokens back to the players and the distribution of the rewards tokens when the game ends.
- Chainlink Price Feeds are used for the calculation of the price of the LP Tokens in USD. This allow the DEXes to configure a stable value in USD which will be reflected in amount of LP tokens required to participate in their games. 
- Our sample frontend interface was built using NextJS, Moralis for the wallet interactions and Ethers.js for the smart contract calls.
- Pixel-art asset pack from [sprout-lands](https://cupnooble.itch.io/sprout-lands-asset-pack)

## What's next for Liquidity Wars
- Accept more LP tokens or Non-Fungible tokens that reflect liquidity and assign each token to specific nations (orc, elves, human, dwarfs). Each nation will have some special bonuses to troops and buildings. Example: dwarfs will be better in defense and orcs will be better in ofense
- Provide fully configurable game and strategies - that allows different DEXes to configure multiple games as they wish (game duration, additional rewards, allowed LP tokens). It will be achieved by using low-level solidity encoded calldata.
- Introduce tradeable ERC1155 tokens with metadata stored on IPFS which creates some bonuses to the game.
- Introduce special building which will provide some bonuses basing on the LP price to nation associated with this LP token.
  
Notice: More specific functionalities which can be done is mentioned [here](https://github.com/Liquidity-Wars/front-end/blob/main/TODO.md) and [here](https://github.com/Liquidity-Wars/smart-contract/blob/main/TODO.md)

## Contracts and structure
Contracts are deployed on Mumbai network and are divided into few parts depending on its functionality.

### LiquidityWarsConfig
Contract contains some calibratable values like: duration of the game, acceptable LP tokens and actual addresses to the **Strategies, LiquidityWars and LiquidityVault** contracts.

Address: [0xe42Db0da865B7252d05999a4d9C5477504D488Ca](https://mumbai.polygonscan.com/address/0xe42Db0da865B7252d05999a4d9C5477504D488Ca#code)

### LiquidityVault
Contract is responsible for deposits, starting and finishing game by interaction with **LiquidityWars** and interaction with **Strategies** contract in order to deposit and withdraw staked LPs with acrued yield.

Address: [0x58dd6859F72AC18f4121488f5ec1578ab489EAAb](https://mumbai.polygonscan.com/address/0x58dd6859F72AC18f4121488f5ec1578ab489EAAb#code)

### LiquidityWars
Contract contains in-game functionalities like resource distribution, building upgrades and battle system. It allows players to interact with game in transparent fashion.

Address: [0xD66539E99320FdA2628c4DdA97DA212d126B8Ca5](https://mumbai.polygonscan.com/address/0xD66539E99320FdA2628c4DdA97DA212d126B8Ca5#code)

### Strategies
Contract contains different strategies which generate the yield basing on deposited LP tokens. For demo purpose the active strategy just generate it's own ERC20 token called REWARDS in order to reflect how it will work on the mainnet.

Address: [0x255577ea5D593fc54Ed8dB9dc16F54f5d9Df4A75](https://mumbai.polygonscan.com/address/0x255577ea5D593fc54Ed8dB9dc16F54f5d9Df4A75#code)

### LiquidityWarsVrf
Contract is involved into randomization of the game. It provides random factors for battle system.

Address: [0x3D79dd115CA215C2f07aD280cf151EA46C1172Dc](https://mumbai.polygonscan.com/address/0x3D79dd115CA215C2f07aD280cf151EA46C1172Dc#code)

### SendMeDemoLps
Contract is only for demo purpose and allows to obtain LP tokens in very easy manner for demo play.

Address: [0xd2f2B6716E0Bd3b8044daDcD58A4d51Eb6C1dfa4](https://mumbai.polygonscan.com/address/0xd2f2B6716E0Bd3b8044daDcD58A4d51Eb6C1dfa4#code)

## Links
Website:
https://liquiditywars.xyz/

Presentation videos:
https://www.youtube.com/watch?v=QyaLId1ARRg