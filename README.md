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

# Overview

Quests Protocol is a protocol to distribute token rewards for completing on-chain tasks.

*Please provide some context about the code being audited, and identify any areas of specific concern in reviewing the code. (This is a good place to link to your docs, if you have them.)*

# Scope

| Contract Name     | SLOC | Purpose                                                                                                                                                                                                        |
|-------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| QuestFactory      | 130  | This is the main factory where Quests get deployed from.                                                                                                                                                       |
| RabbitHoleReceipt | 120  | This is the receipt contract. An ERC-721 contract that a user has the ability to mint once they have completed an on-chain action. To claim a reward you must own a Receipt that has not claimed a reward yet. |
| Quest             | 94   | This is the parent class for Quests. This encapsulates a lot of the shared logic in the Erc20Quest & Erc1155Quest                                                                                              |
| RabbitHoleTickets | 78   | This is an 1155 reward contract used by the RabbitHole team.                                                                                                                                                   |
| Erc20Quest        | 67   | This is a Quest where the reward to be claimed is an ERC-20 token.                                                                                                                                             |
| Erc1155Quest      | 45   | This is a Quest where the reward to be claimed is an ERC-1155 token.                                                                                                                                           |
| ReceiptRenderer   | 40   | This is an on-chain renderer for our ERC-721 Receipt contract                                                                                                                                                  |
| TicketRenderer    | 34   | This is an on-chain renderer for our ERC-1155 reward (RabbitHoleTickets) contract                                                                                                                              |
| IQuest            | 16   | This is a Quest interface                                                                                                                                                                                      |
| IQuestFactory     | 14   | This is a Quest Factory interface      

& all their inherited / library contracts.

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
- Total SLoC for these contracts?:  638
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
yarn 
yarn compile
```

### Run all tests:

```bash
yarn test
```

### Run test coverage report:

```bash
yarn test:coverage
```

