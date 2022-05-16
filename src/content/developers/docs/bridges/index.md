---
title: Bridges
description: An overview of bridging for developers
lang: en
sidebar: true
---

With the proliferation of L1 blockchains and L2 [scaling](/developers/docs/scaling/) solutions, alongside an ever-growing number of decentralized applications going cross-chain, the need for communication and asset movement across chains has become an essential part of network infrastructure. Different types of bridges exist to help make this possible.

This is where blockchain bridges come in.

## Need for bridges {#need-for-bridges}

Bridges exist to connect blockchain networks. They enable connectivity and interoperability between blockchains.

Blockchains exist in siloed environments, meaning there is no way for blockchains to trade and communicate with other blockchains naturally. As a result, while there could be significant activity and innovation within an ecosystem, it is limited by the lack of connectivity and interoperability with other ecosystems.

Bridges offer a way for isolated blockchain environments to connect with each other. They establish a transportation route between blockchains where tokens, messages, arbitrary data, and even [smart contract](/developers/docs/smart-contracts/) calls can be transferred from one chain to another.

## Benefits of bridges {#benefits-of-bridges}

Put simply, bridges unlock developer potential by allowing blockchain networks to exchange data and move assets between them.

Blockchains have unique strengths, weaknesses, and approaches to building applications (such as speed, throughput, costliness, etc.). Bridges help the development of the overall crypto ecosystem by enabling blockchains to leverage the innovations of each other.

Moreover, bridges unlock new use cases and possibilities for both users and developers. For example, users can now move assets across different ecosystems, making them more productive. For developers and protocols, bridges open up an almost limitless amount of possibilities by expanding the design space for [dApps](/developers/docs/dapps/) across multiple crypto ecosystems.

## How do bridges work? {#how-do-bridges-work}

While there are many [types of bridge designs](https://blog.li.fi/what-are-blockchain-bridges-and-how-can-we-classify-them-560dc6ec05fa), three ways to facilitate the cross-chain transfer of assets stand out:

- **Lock and Mint –** Lock assets on the source chain and mint assets on the destination chain.
- **Burn and Mint –** Burn assets on the source chain and mint assets on the destination chain.
- **Atomic Swaps –** Swap assets on the source chain for assets on the destination chain.

## Bridge types {#bridge-types}

Bridges can usually be classified into one of the following buckets:

- **Native Bridges –** These bridges are typically built to bootstrap liquidity on a particular blockchain, making it easier for users to move funds to the ecosystem. For example, the Avalanche Bridge is built to make it convenient for users to bridge from [Ethereum](/developers/docs/intro-to-ethereum/) to Avalanche. Other such bridges include Polygon PoS Bridge, Arbitrum Bridge, etc.
- **Validator or Oracle Based Bridges –** These bridges rely on an external validator set or oracles to validate cross-chain transfers. Examples: Multichain and Across.
- **Generalized Message Passing Bridges –** These bridges can transfer assets, along with messages and arbitrary data across chains. Examples: Nomad and LayerZero.
- **Liquidity Networks –** These bridges primarily focus on transferring assets from one chain to another via atomic swaps. Generally, they don’t support cross-chain message passing. Examples: Connext and Hop.

## Trade-offs to consider {#trade-offs}

With bridges, there are no perfect solutions. Rather, there are only trade-offs made to fulfill a purpose. Developers and users can evaluate bridges based on the following factors:

- **Security –** Who verifies the system? Bridges secured by external validators are typically less secure than bridges that are locally or natively secured by the blockchain’s validators.
- **Convenience –** How long does it take to complete a transaction, and how many transactions did a user need to sign? For a developer, how long does it take to integrate a bridge, and how complex is the process?
- **Connectivity –** What are the different destination chains a bridge can connect (i.e., rollups, sidechains, other layer 1 blockchains, etc.), and how hard is it to integrate a new blockchain?
- **Ability to pass more complex data –** Can a bridge enable the transfer of messages and more complex arbitrary data across chains, or does it only support cross-chain asset transfers?
- **Cost-Effectiveness –** How much does it cost to transfer assets across chains via a bridge? Typically, bridges charge a fixed or variable fee depending on gas costs and the liquidity of specific routes. It is also critical to evaluate the cost-effectiveness of a bridge based on the capital required to ensure its security.

At a high level, bridges can be categorized as trusted and trustless.

- **Trusted –** Trusted bridges are externally verified. They use an external set of verifiers (Federations with multi-sig, multi-party computation systems, oracle network) to send data across chains. As a result, they can offer great connectivity and enable fully generalized message passing across chains. They also tend to perform well with speed and cost-effectiveness. This comes at the cost of security, as users have to rely on the security of the bridge.
- **Trustless –** These bridges rely on the blockchains they are connecting and their validators to transfer messages and tokens. They are 'trustless' because they do not add new trust assumptions (in addition to the blockchains). As a result, trustless bridges are considered to be more secure than trusted bridges. 

To evaluate trustless bridges based on other factors, we must break them down into generalized message passing bridges and liquidity networks.

  - **Generalized Message Passing Bridges –** These bridges excel with security and the ability to transfer more complex data across chains. Typically, they are also good with cost-effectiveness. However, these strengths generally come at the cost of connectivity for light client bridges (ex: IBC) and speed drawbacks for optimistic bridges (ex: Nomad) that use fraud proofs.
  - **Liquidity Networks –** These bridges use atomic swaps for transferring assets and are locally verified systems (i.e., they use the underlying blockchains’ validators to verify transactions). As a result, they excel with security and speed. Moreover, they are considered comparatively cost-effective and offer good connectivity. However, the major tradeoff is their ability to pass more complex data – as they don’t support cross-chain message passing.

## Risk with bridges {#risk-with-bridges}

Bridges account for the top three [biggest hacks in DeFi](https://rekt.news/leaderboard/) and are still in the early stages of development. Using any bridge carries the following risks:

- **Smart Contract Risk –** While many bridges have successfully passed audits, all it takes is one flaw in a smart contract for assets to be exposed to hacks (ex: [Solana’s Wormhole Bridge](https://rekt.news/wormhole-rekt/)).
- **Technology Risk –** Given the complexity of bridge operations, there is a possibility of technology risks like software failure, buggy code, human error, spam, and malicious attacks.
- **Systematic Financial Risks** – Many bridges use wrapped assets to mint canonical versions of the original asset on a new chain. This exposes the ecosystem to systematic risk, as we have seen wrapped versions of tokens exploited.
- **Trusted Third-Party Risk –** Some bridges utilize a trusted design that requires users to rely on the assumption that validators will not collude to steal user funds. The need for users to trust these third-party actors exposes them to risks such as rug pulls, censorship, and other malicious activities.
- **Open Issues –** Given that bridges are in the nascent stages of development, there are many unanswered questions related to how bridges will perform in different market conditions, like times of network congestion and during unforeseen events such as network-level attacks or state rollbacks. This uncertainty poses certain risks, the degree of which is still unknown.

## How can dapps use bridges? {#how-can-dapps-use-bridges}

Here are some practical applications that developers can consider about bridges and taking their dApp cross-chain:

### Integrating bridges {#integrating-bridges}

For developers, there are many ways to add support for bridges:

1. **Building your own bridge –** Building a secure and reliable bridge is not easy, especially if you take a more trust-minimized route. Moreover, it requires years of experience and technical expertise related to scalability and interoperability studies. Additionally, it would require a hands-on team to maintain a bridge and attract sufficient liquidity to make it feasible.
2. **Showing users multiple bridge options –** Many dApps require users to have their native token to interact with them. To enable users to access their tokens, they offer different bridge options on their website. However, this method is a quick fix to the problem as it takes the user away from the dApp interface and still requires them to interact with other dApps and bridges. This is a cumbersome onboarding experience with the increased scope of making mistakes.
3. **Integrating a bridge –** This solution doesn’t require the dApp to send users to the external bridge and DEX interfaces. It allows dApps to improve the user onboarding experience. However, this approach has its limitations:
   - Assessment and maintenance of bridges are hard and time-consuming.
   - Selecting one bridge creates a single point of failure and dependency.
   - The dApp is limited by the bridge’s capabilities.
   - Bridges alone might not be enough. dApps might need DEXs to offer more functionality such as cross-chain swaps.
4. **Integrating multiple bridges –** This solution solves many problems associated with integrating a single bridge. However, it also has limitations, as integrating multiple bridges is resource-consuming and creates technical and communication overheads for developers – the scarcest resource in crypto.
5. **Integrating a bridge aggregator –** Another option for dApps is integrating a bridge aggregation solution that gives them access to multiple bridges. Bridge aggregators inherit the strengths of all the bridges and thus are not limited by any single bridge’s capabilities. Notably, the bridge aggregators typically maintain the bridge integrations, which saves the dApp from the hassle of staying on top of the technical and operational aspects of a bridge integration.

   That being said, bridge aggregators also have their limitations. For instance, while they can offer more bridge options, many more bridges are typically available in the market other than those offered on the aggregator's platform. Moreover, just like bridges, bridge aggregators are also exposed to smart contracts and technology risks (more smart contracts = more risks).

If a dApp goes down the route of integrating a bridge or an aggregator, there are different options based on how deep the integration is meant to be. For instance, if it’s only a front-end integration to improve the user onboarding experience, a dApp would integrate the widget. However, if the integration is to explore deeper cross-chain strategies like staking, yield farming, etc., the dApp integrates the SDK or API.

### Deploying a dapp on multiple chains {#deploying-a-dapp-on-multiple-chains}

To deploy a dApp on multiple chains, developers can use development platforms like Alchemy, Hardhat, Truffle, etc. Typically, these platforms come with composable plugins that can enable dApps to go cross-chain. For instance, developers can use a deterministic deployment proxy offered by the hardhat-deploy plugin.

### Monitoring contract activity across chains {#monitoring-contract-activity-across-chains}

To monitor contract activity across chains, developers can use subgraphs and developer platforms like Tenderly to observe smart contracts in real-time. Such platforms also have tools that offer greater data monitoring functionality for cross-chain activities, such as checking for events emitted by contracts, etc.

## Further reading {#further-reading}

- [Blockchain Bridges](/en/bridges/) – ethereum.org
- [Blockchain Bridges: Building Networks of Cryptonetworks](https://medium.com/1kxnetwork/blockchain-bridges-5db6afac44f8) Sep 8, 2021 – Dmitriy Berenzon
- [The Interoperability Trilemma](https://blog.connext.network/the-interoperability-trilemma-657c2cf69f17) Oct 1, 2021 – Arjun Bhuptani
- [Clusters: How Trusted & Trust-Minimized Bridges Shape the Multi-Chain Landscape](https://blog.celestia.org/clusters/) Oct 4, 2021 – Mustafa Al-Bassam
- [LI.FI: With Bridges, Trust is a Spectrum](https://blog.li.fi/li-fi-with-bridges-trust-is-a-spectrum-354cd5a1a6d8) Apr 28, 2022 – Arjun Chand

Additionally, here are some insightful presentations by [James Prestwich](https://twitter.com/_prestwich) that can help develop a deeper understanding of bridges:

- [Building Bridges, Not Walled Gardens](https://youtu.be/ZQJWMiX4hT0)
- [Breaking Down Bridges](https://youtu.be/b0mC-ZqN8Oo)
- [Why are the Bridges Burning](https://youtu.be/c7cm2kd20j8)