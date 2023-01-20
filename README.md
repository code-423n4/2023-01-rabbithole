# ✨ So you want to sponsor a contest

This `README.md` contains a set of checklists for our contest collaboration.

Your contest will use two repos: 
- **a _contest_ repo** (this one), which is used for scoping your contest and for providing information to contestants (wardens)
- **a _findings_ repo**, where issues are submitted (shared with you after the contest) 

Ultimately, when we launch the contest, this contest repo will be made public and will contain the smart contracts to be reviewed and all the information needed for contest participants. The findings repo will be made public after the contest report is published and your team has mitigated the identified issues.

Some of the checklists in this doc are for **C4 (🐺)** and some of them are for **you as the contest sponsor (⭐️)**.

---

# Repo setup

## ⭐️ Sponsor: Add code to this repo

- [ ] Create a PR to this repo with the below changes:
- [ ] Provide a self-contained repository with working commands that will build (at least) all in-scope contracts, and commands that will run tests producing gas reports for the relevant contracts.
- [ ] Make sure your code is thoroughly commented using the [NatSpec format](https://docs.soliditylang.org/en/v0.5.10/natspec-format.html#natspec-format).
- [ ] Please have final versions of contracts and documentation added/updated in this repo **no less than 24 hours prior to contest start time.**
- [ ] Be prepared for a 🚨code freeze🚨 for the duration of the contest — important because it establishes a level playing field. We want to ensure everyone's looking at the same code, no matter when they look during the contest. (Note: this includes your own repo, since a PR can leak alpha to our wardens!)


---

## ⭐️ Sponsor: Edit this README

Under "SPONSORS ADD INFO HERE" heading below, include the following:

- [ ] Modify the bottom of this `README.md` file to describe how your code is supposed to work with links to any relevent documentation and any other criteria/details that the C4 Wardens should keep in mind when reviewing. ([Here's a well-constructed example.](https://github.com/code-423n4/2022-08-foundation#readme))
  - [ ] When linking, please provide all links as full absolute links versus relative links
  - [ ] All information should be provided in markdown format (HTML does not render on Code4rena.com)
- [ ] Under the "Scope" heading, provide the name of each contract and:
  - [ ] source lines of code (excluding blank lines and comments) in each
  - [ ] external contracts called in each
  - [ ] libraries used in each
- [ ] Describe any novel or unique curve logic or mathematical models implemented in the contracts
- [ ] Does the token conform to the ERC-20 standard? In what specific ways does it differ?
- [ ] Describe anything else that adds any special logic that makes your approach unique
- [ ] Identify any areas of specific concern in reviewing the code
- [ ] Optional / nice to have: pre-record a high-level overview of your protocol (not just specific smart contract functions). This saves wardens a lot of time wading through documentation.
- [ ] See also: [this checklist in Notion](https://code4rena.notion.site/Key-info-for-Code4rena-sponsors-f60764c4c4574bbf8e7a6dbd72cc49b4#0cafa01e6201462e9f78677a39e09746)
- [ ] Delete this checklist and all text above the line below when you're ready.

---

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

[ ⭐️ SPONSORS ADD INFO HERE ]

# Overview

*Please provide some context about the code being audited, and identify any areas of specific concern in reviewing the code. (This is a good place to link to your docs, if you have them.)*

# Scope

*List all files in scope in the table below (along with hyperlinks) -- and feel free to add notes here to emphasize areas of focus.*

*For line of code counts, we recommend using [cloc](https://github.com/AlDanial/cloc).* 

| Contract | SLOC | Purpose | Libraries used |  
| ----------- | ----------- | ----------- | ----------- |
| [contracts/folder/sample.sol](contracts/folder/sample.sol) | 123 | This contract does XYZ | [`@openzeppelin/*`](https://openzeppelin.com/contracts/) |

## Out of scope

*List any files/contracts that are out of scope for this audit.*

# Additional Context

*Describe any novel or unique curve logic or mathematical models implemented in the contracts*

*Sponsor, please confirm/edit the information below.*

## Scoping Details 
```
- If you have a public code repo, please share it here: https://github.com/rabbitholegg/quest-protocol
- How many contracts are in scope?: 5   
- Total SLoC for these contracts?:  429
- How many external imports are there?: 18 
- How many separate interfaces and struct definitions are there for the contracts within scope?: 11 
- Does most of your code generally use composition or inheritance?: Yes. Only inheritance is abstraction of Quest Types into a parent Quest  
- How many external calls?: 1   
- What is the overall line coverage percentage provided by your tests?: 89 
- Is there a need to understand a separate part of the codebase / get context in order to audit this part of the protocol?: Yes  
- Please describe required context: There is an ECDSA signature that provides proof of action on chain from our own event indexer  
- Does it use an oracle?: Yes, described in previous question.
- Does the token conform to the ERC20 standard?: No, although one Quest type does hold ERC20 in contract. 
- Are there any novel or unique curve logic or mathematical models?: N/A
- Does it use a timelock function?: Yes - there is a timelock to let users claim at 12pm each day after their interaction. 
- Is it an NFT?: There is one NFT contract as part of this (RabbitholeReceipt) and the 1155 Quest also allows for usage of 1155 distribution
- Does it have an AMM?: No
- Is it a fork of a popular project?: No  
- Does it use rollups?: No
- Is it multi-chain?: Yes
- Does it use a side-chain?: Yes
```

# Tests

*Provide every step required to build the project from a fresh git clone, as well as steps to run the tests with a gas report.* 

*Note: Many wardens run Slither as a first pass for testing.  Please document any known errors with no workaround.* 


# Quest Protocol

[![Tests](https://github.com/rabbitholegg/quest-protocol/workflows/Tests/badge.svg)](https://github.com/rabbitholegg/quest-protocol/actions?query=workflow%3ATests)
[![Lint](https://github.com/rabbitholegg/quest-protocol/workflows/Lint/badge.svg)](https://github.com/rabbitholegg/quest-protocol/actions?query=workflow%3ALint)

## Overview

Quests Protocol is a protocol to distribute token rewards for completing on-chain tasks.

![img.png](img.png)

---

## Table of Contents

- [Quest Protocol](https://github.com/rabbitholegg/quest-protocol#quest-protocol)
    - [Table of Contents](https://github.com/rabbitholegg/quest-protocol#table-of-contents)
    - [Documentation](https://github.com/rabbitholegg/quest-protocol#documentation)
    - [Layout](https://github.com/rabbitholegg/quest-protocol#layout)
    - [Deployments](https://github.com/rabbitholegg/quest-protocol#deployments)
    - [Install](https://github.com/rabbitholegg/quest-protocol#install)
    - [Testing](https://github.com/rabbitholegg/quest-protocol#testing)
    - [Upgrading](https://github.com/rabbitholegg/quest-protocol#upgrading)
    - [Audits](https://github.com/rabbitholegg/quest-protocol#audits)
    - [Bug Bounty](https://github.com/rabbitholegg/quest-protocol#bug-bounty)
    - [License](https://github.com/rabbitholegg/quest-protocol/#license)

---
## Documentation

For more information on all docs related to the Quest Protocol, see the documentation directory [here](./docs/).

- [Overview](./docs/overview.md)
- [Quest Claim](./docs/quest-claim.md)
- [Quest Create](./docs/quest-create.md)
- [Audit Endpoints](./docs/audit-endpoints.md)

---

## Layout
Generated with:
```bash
tree --filelimit 20 -I artifacts -I contracts-upgradeable -I factories -I typechain-types -I cache -I img.png
```

```
├── LICENSE
├── README.md
├── audits
├── contracts
│   ├── Erc1155Quest.sol
│   ├── Erc20Quest.sol
│   ├── Quest.sol
│   ├── QuestFactory.sol
│   ├── RabbitHoleReceipt.sol
│   ├── SampleERC20.sol
│   ├── SampleErc1155.sol
│   ├── interfaces
│   │   └── IQuest.sol
│   └── test
│       └── TestERC20.sol
├── coverage.json
├── docs
│   ├── overview.md
│   ├── quest-claim.md
│   └── quest-create.md
├── hardhat.config.ts
├── node_modules  [488 entries exceeds filelimit, not opening dir]
├── package.json
├── scripts
│   ├── deployQuestFactory.js
│   ├── deployRabbitHoleReceipt.js
│   ├── upgradeQuestFactory.js
│   └── upgradeRabbitHoleReceipt.js
├── test
│   ├── Erc1155Quest.spec.ts
│   ├── Erc20Quest.spec.ts
│   ├── Quest.spec.ts
│   ├── QuestFactory.spec.ts
│   ├── RabbitHoleReceipt.spec.ts
│   ├── SampleErc1155.spec.ts
│   ├── SampleErc20.spec.ts
│   └── types.ts
├── tsconfig.json
├── waffle.json
└── yarn.lock
```

---

## Deployments

|Chain           |Quest Factory Contract                    |
|----------------|------------------------------------------|
|Ethereum        |0x0                                       |
|Goerli          |0x32c2231d0977422db6eA5aA19d31d210d6512CF8|
|Polygon Mainnet |0x0                                       |
|Polygon Testnet |0x0                                       |
|Optimism        |0x0                                       |
|Optimism Testnet|0x0                                       |
|Arbitrum        |0x0                                       |
|Arbitrum Testnet|0x0                                       |

---

## Contracts

The main contracts involved in this phase are:

- `Quest Factory` ([code](./contracts/QuestFactory.sol))
    - Creates new `Quest` instances of an ERC-1155 reward Quest or ERC-20 reward Quest.
- `RabbitHole Receipt` ([code](./contracts/RabbitHoleReceipt.sol))
    - An ERC-721 contract that acts as a proof of on-chain activity. Claimed via usage of ECDSA sig/hash
- `ERC-20 Quest` ([code](./contracts/Erc20Quest.sol))
    - A Quest in which the reward is an ERC-20 token
- `ERC-1155 Quest` ([code](./contracts/Erc1155Quest.sol))
    - A Quest in which the reward is an ERC-1155 token

---
## Patterns

The contracts use two main patterns.

### Factory Pattern
More reading [here](https://www.tutorialspoint.com/design_pattern/factory_pattern.htm)

![image](https://user-images.githubusercontent.com/14314818/213348232-4bc57639-d281-41e7-a0c3-c3886d8e0be9.png)

### Dependency Injection
More reading [here](https://www.freecodecamp.org/news/a-quick-intro-to-dependency-injection-what-it-is-and-when-to-use-it-7578c84fa88f/)
![image](https://user-images.githubusercontent.com/14314818/213348583-fc0a94ec-cc3f-4730-90d2-5503d027c7b8.png)

### Factory Creation Pattern
More reading [here](https://dev.to/jamiescript/design-patterns-in-solidity-1i28#factory)

---

## Install

### Install dependencies

```bash
yarn
```

### Compile Contracts
```bash
yarn compile
```


---

## Testing

### Run all tests:

```bash
yarn test
```

### Run test coverage report:

```bash
yarn test:coverage
```

---

## Upgrading

The Quest Factory is an upgradable contract. Over time as the space evolves there will be more than just ERC-20 or
ERC-1155 rewards and we want to be non-limiting in our compatibility.

1. `yarn hardhat run --network goerli scripts/upgradeQuestFactory.js` or `scripts/upgradeRabbitHoleReceipt.js` and
   replace the network with `mainnet` if you are upgrading on mainnet.
    1. If you get an error like `NomicLabsHardhatPluginError: Failed to send contract verification request.` It's
       usually because the contract wasn't deployed by the time verification ran. You can run verification again
       with `yarn hardhat verify --network goerli IMPLENTATION_ADDRESS` where the implementation address is in the
       output of the upgrade script.
2. go to https://defender.openzeppelin.com/#/admin and approve the upgrade proposal (the link is also in the output of
   the upgrade script)
3. After the upgrade proposal is approved, create a PR with the updates to the .openzeppelin/[network-name].json file.

---

## Audits

The following auditors reviewed the protocol. You can see reports in `/audits` directory:

- Code4rena TBD (report [here](/audits/))

---
## Bug Bounty

All contracts except tests, interfaces, dependencies are in scope and eligible for the Quest Protocol Bug Bounty program.

The rubric we use to determine bug bounties is as follows:

| **Level**   | **Example**                                                                                                                                                                                      | **Maximum Bug Bounty** |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------- |
| 6. Severe   | - Draining or freezing of holdings protocol-wide (e.g. draining token distributor, economic attacks, reentrancy, MEV, logic errors)                                                              | Let's talk             |
| 5. Critical | - Contracts with balances can be exploited to steal holdings under specific conditions (e.g. bypass guardrails to transfer precious NFT from parties, user can steal their party's distribution) | Up to 25 ETH           |
| 4. High     | - Contracts temporarily unable to transfer holdings<br>- Users spoof each other                                                                                                                  | Up to 10 ETH           |
| 3. Medium   | - Contract consumes unbounded gas<br>- Griefing, denial of service (i.e. attacker spends as much in gas as damage to the contract)                                                               | Up to 5 ETH            |
| 2. Low      | - Contract fails to behave as expected, but doesn't lose value                                                                                                                                   | Up to 1 ETH            |
| 1. None     | - Best practices                                                                                                                                                                                 |                        |

Any vulnerability or bug discovered must be reported only to the following email: [security@rabbithole.gg](mailto:security@rabbithole.gg).

---
## License
The primary license for the Quest Protocol is the GNU General Public License 3.0 (GPL-3.0), see [LICENSE](./LICENSE).

Several interface/dependencies files from other sources maintain their original license (as indicated in their SPDX header).
All files in test/ remain unlicensed (as indicated in their SPDX header).
