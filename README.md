# RabbitHole contest details

- Total Prize Pool: $36,500 USDC
  - HM awards: $25,500 USDC
  - QA report awards: $3,000 USDC
  - Gas report awards: $1,500 USDC
  - Judge + presort awards: $6,000 USDC
  - Scout awards: $500 USDC
- Join [C4 Discord](https://discord.gg/code4rena) to register
- Submit findings [using the C4 form](https://code4rena.com/contests/2023-01-rabbithole-contest/submit)
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts January 25, 2023 20:00 UTC
- Ends January 30, 2023 20:00 UTC

## C4udit / Publicly Known Issues

The C4audit output for the contest can be found [here](add link to report) within an hour of contest opening.

*Note for C4 wardens: Anything included in the C4udit output is considered a publicly known issue and is ineligible for awards.*

## Cloning the repo

Please note that the contest's code is hosted on an external repo. To fetch it, use one of the following methods:

- Cloning using SSH:

```bash
git clone --recurse-submodules git@github.com:code-423n4/2023-01-rabbithole.git
```

- Cloning using HTTPS:

```bash
git clone --recurse-submodules https://github.com/code-423n4/2023-01-rabbithole.git
```

- Getting the submodules if cloning was done without `--recurse-submodules`:

```bash
git submodule update --init --recursive
```

# Overview

**Quests Protocol is a protocol to distribute token rewards for completing on-chain tasks.**

We're releasing five new contracts that are in scope for the audit (more inherited contracts included below):

- [Quest Factory](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/QuestFactory.sol): An upgradable factory that creates a new ERC-20 or ERC-1155 Quest. This follows the factory method & factory creation patterns. This also houses logic on aggregating Quests & minting receipts
- [ERC-20 Quest](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/Erc20Quest.sol): A Quest that rewards an on-chain action with an ERC-20 token. You must own an unclaimed receipt to be able to claim the reward.
- [ERC-1155 Quest](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/Erc1155Quest.sol): A Quest that rewards an on-chain action with an ERC-1155 token. You must own an unclaimed receipt to be able to claim the reward.
- [Receipt](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/RabbitHoleReceipt.sol): An ERC-721 contract that is able to be claimed by a user once they have completed an on-chain task. This must be held (and unclaimed) to claim a reward.
- [Ticket](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/RabbitHoleTickets.sol): An ERC-1155 contract that is used by the RabbitHole team for ERC-1155 Quests. AKA this is an ERC-1155 Reward.

## Create Quest Flow
![image](https://user-images.githubusercontent.com/14314818/214160118-16239aa0-18ca-4963-b812-df4f26153a94.png)

## Claim Flow
![image](https://user-images.githubusercontent.com/14314818/214354756-0af7e34d-746e-4429-8b55-8eb6d8bb1e31.png)

## ERC-20 Money Flow
![image](https://user-images.githubusercontent.com/14314818/214363528-84f9d0fd-ea28-4233-a43e-7f67afc0fc5c.png)


See our full suite of documentation [here](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/README.md#quest-protocol).

# Scope

| Contract Name     | SLOC | Purpose                                                                                                                                                                                                        |
|-------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [QuestFactory](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/QuestFactory.sol)      | 162  | This is the main factory where Quests get deployed from.                                                                                                                                                       |
| [RabbitHoleReceipt](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/RabbitHoleReceipt.sol) | 137  | This is the receipt contract. An ERC-721 contract that a user has the ability to mint once they have completed an on-chain action. To claim a reward you must own a Receipt that has not claimed a reward yet. |
| [Quest](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/Quest.sol)             | 100   | This is the parent class for Quests. This encapsulates a lot of the shared logic in the Erc20Quest & Erc1155Quest                                                                                              |
| [RabbitHoleTickets](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/RabbitHoleTickets.sol) | 82   | This is an 1155 reward contract used by the RabbitHole team.                                                                                                                                                   |
| [Erc20Quest](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/Erc20Quest.sol)        | 67   | This is a Quest where the reward to be claimed is an ERC-20 token.                                                                                                                                             |
| [Erc1155Quest](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/Erc1155Quest.sol)      | 45   | This is a Quest where the reward to be claimed is an ERC-1155 token.                                                                                                                                           |
| [ReceiptRenderer](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/ReceiptRenderer.sol)   | 90   | This is an on-chain renderer for our ERC-721 Receipt contract                                                                                                                                                  |
| [TicketRenderer](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/TicketRenderer.sol)    | 34   | This is an on-chain renderer for our ERC-1155 reward (RabbitHoleTickets) contract                                                                                                                              |
| [IQuest](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/interfaces/IQuest.sol)            | 19   | This is a Quest interface                                                                                                                                                                                      |
| [IQuestFactory](https://github.com/rabbitholegg/quest-protocol/blob/8c4c1f71221570b14a0479c216583342bd652d8d/contracts/interfaces/IQuestFactory.sol)     | 16   | This is a Quest Factory interface

We would like to call out extra attention to `QuestFactory.mintReceipt` (users should only be able to claim one receipt), `Quest.claim` - users should only be able to claim the amount of rewards for number of receipts they have. Note - users could claim a receipt, sell it on secondary (not claim reward) and a user could end up with multiple receipts that can claim multiple rewards. Also following funds flow lifecycle throughout the contracts.

## Out of scope

- /contracts/test/*
- @openzeppelin/*

# Additional Context

- For protocol fee we use basis points (BPS). You can read more on it [here](https://www.investopedia.com/terms/b/basispoint.asp) but the TLDR; is 10_000 is 100%. So 2.5% fee would be 250 BPS.
- Our QuestFactory will be an upgradeable proxy allowing us to add more features overtime. For an overview of the upgrade pattern, refer to the [OpenZeppelin documentation](https://docs.openzeppelin.com/upgrades-plugins/1.x/writing-upgradeable).

## Scoping Details

```
- If you have a public code repo, please share it here: https://github.com/rabbitholegg/quest-protocol
- How many contracts are in scope?: 10   
- Total SLoC for these contracts?:  752
- How many external imports are there?: 18 
- How many separate interfaces and struct definitions are there for the contracts within scope?: 11 
- Does most of your code generally use composition or inheritance?: Yes. Only inheritance is abstraction of Quest Types into a parent Quest  
- How many external calls?: 1   
- What is the overall line coverage percentage provided by your tests?: 89 
- Is there a need to understand a separate part of the codebase / get context in order to audit this part of the protocol?: Yes  
- Please describe required context: There is an ECDSA signature that provides proof of action on chain from our own event indexer  
- Does it use an oracle?: Yes (sorta), described in previous question.
- Does the token conform to the ERC20 standard?: No
- Are there any novel or unique curve logic or mathematical models?: N/A
- Does it use a timelock function?: No
- Is it an NFT?: There are two NFT contracts as part of this. RabbitHoleReceipt is an ERC-721 contract that distributes receipts for on-chain usage. RabbitHoleTickets is an ERC-1155 that is a reward for an ERC-1155 Quest. 
- Does it have an AMM?: No
- Is it a fork of a popular project?: No  
- Does it use rollups?: No
- Is it multi-chain?: Yes (but currently just deployed to Goerli)
- Does it use a side-chain?: Yes (same note as above, will go on Polygon)
```

# Tests

### Setup

```bash
cd quest-protocol
yarn 
yarn compile
```

### Run all tests

```bash
yarn test
```

### Run test coverage report

```bash
yarn test:coverage
```

### Run gas test:

```bash
yarn test:gas-stories
```

### Slither

Slither works from the root directory. We also have a GitHub action you can find on our repo linked through in the docs.

```bash
slither .
```
