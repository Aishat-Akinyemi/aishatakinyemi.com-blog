# The Need for Decentralized Web3 API  Providers

## Introduction

A blockchain is a distributed deterministic single-state machine maintained by a peer-to-peer network of nodes. The nodes in a blockchain network run the blockchain client’s software and store the network's transaction data.

### Types of blockchain nodes

There are different types of blockchain nodes. Full nodes run the state machine starting from the genesis file. They contain all network transactions from the genesis block. Light nodes, however, do not store the entire state of the blockchain—they only store the block headers.

Validator nodes are full nodes that take part in the network consensus. Remote Procedure Call (RPC) nodes are full nodes acting as the data access layer of the blockchain network. RPC nodes do not partake in the consensus mechanism. 

### RPC and RPC nodes

RPC nodes are the gateway to the blockchain network. When a user initiates a transaction, the request is submitted into the blockchain pool by an RPC node. The same thing happens when a user/application queries blockchain data.

Blockchain interactions involve sending network requests to specific JSON-RPC API methods of the blockchain client. Nodes have their RPC endpoints enabled so they can serve these RPC requests. Although any full node in a blockchain network can relay these requests, RPC nodes are dedicated to relaying them for security and performance reasons.

**What is RPC?**

[Remote Procedure Call](https://www.w3.org/History/1992/nfs_dxcern_mirror/rpc/doc/Introduction/WhatIs.html) is a communication technique used in distributed computing. RPC abstracts the network communication details such that a program requests a service/subroutine of another system in a different location as if it were a local service.


| ![Remote Procedure Call](https://i.ytimg.com/vi/3HunZHHrk1Q/maxresdefault.jpg) |
|:--:|
| Remote Procedure Call, <i>Anuradha Bhatia</i>|

RPC is the standard client-to-blockchain communication technique in web3 owing to its simplicity and support for batch requests, and it is more suited for distributed computing.

As an example, if you use a Defi application that would interact with Binance Smart Chain (BSC, a [cosmos-sdk based appchain](https://docs.cosmos.network/v0.46/intro/why-app-specific.html#what-are-application-specific-blockchains) built on Cosmos Tendermint), your request is sent through a fullnode that has its tendermint-rpc endpoint exposed—an RPC node. This RPC node handles and serves state query requests, as well as broadcasting transaction requests to validator nodes in the BSC network.

| ![Transaction relay to BSC network through RPC node ](https://media.discordapp.net/attachments/999832818916020275/1002441832116011028/RPC_request_using_cosmos_blockchain.png) |
|:--:|
|Transaction relay to BSC network through RPC node, <i>Aishat Akinyemi</i>| 

## RPC node provisioning

You can run your RPC node in-house if you have systems administration skills, with hardware that meets a blockchain RPC node system specification. Free public RPC nodes (with usage limits) are often used for testing and development. Whereas you would need dedicated RPC nodes for your applications in production. A dedicated RPC endpoint ensures reliability, scalability, and high quality of service.

Provisioning your RPC node comes with challenges such as maintaining the reliability of your nodes, performing upgrades, and node health monitoring. There also needs to be security measures in place to guard against vulnerabilities. 

Scaling RPC nodes as the volume of requests grow has its peculiar challenges. One of the persistent issues faced by teams running more than one node is the issue of data consistency. Node data inconsistency occurs when nodes are out of sync. When some nodes are out of sync, different nodes return different results to the same query. 

The challenges stated above make developers opt for the services of RPC node infrastructure providers. 

## Centralized RPC node providers

Companies like Alchemy, Infura, Quicknode, Blockdeamon, and Ankr, are businesses that specialize in RPC node infrastructure management. These companies provide developers access to synced, up-to-date, highly available, and scalable RPC nodes. 

RPC node providers simplify node spin-up and offer various APIs and analytics such as NFT APIs, request management, transaction history, node requests tracking, and monitoring. The services of RPC node providers are also less costly when compared with in-house node provisioning.

The node inconsistency and data inaccuracy issues described earlier still happen with RPC node providers. Many RPC providers are engineering on solving this problem, as seen with Alchemy's Supernode. Alchemy aims to achieve data accuracy with its [Supernode](https://www.alchemy.com/blog/data-accuracy) product as a direct solution to the node data inaccuracy issue.

|![[Alchemy’s **Benchmarking Node Providers**](https://www.alchemy.com/blog/data-accuracy)](https://assets.website-files.com/6086f3afee58e6a9bb6c8053/62cdab399c1b4a1d2e0cec7b_inconsistent-blocks.png) |
|:--:|
| [Alchemy’s **Benchmarking Node Providers**](https://www.alchemy.com/blog/data-accuracy), <i>Alchemy</i>|

Further issues associated with centralized RPC nodes include:

- The RPC providers with the largest market share (Alchemy, Infura, Quicknode, Blockdeamon) all run on centralized infrastructure that they control. This centralization of blockchain RPC access is antithetical to the core of blockchain: decentralization. Centralizing the infrastructure blockchain applications run on makes these applications less decentralized. 

- RPC providers can monitor and track user requests for various data analytics features they offer. This negates one of the major promises of blockchain technology—anonymity. We can’t promise users privacy when their IP addresses, TLS session tickets, and requests can be tracked and collected. Data collection introduces security and privacy concerns.

- Absence of data verification mechanisms in place to validate the accuracy and consistency of centralized RPC nodes. There is no penalty for RPC providers serving incorrect data, and there is no trustless data correctness/validity proving mechanism. 

- Centralization introduces single points of failure to blockchain solutions. Recent DNS attacks on [Ankr](https://www.coindesk.com/tech/2022/07/01/two-polygon-fantom-front-ends-hit-by-dns-attack/) RPC network compromised Polygon and Fantom RPC gateways, [Infura](https://twitter.com/MetaMask/status/1517531050246868993?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1517531050246868993%7Ctwgr%5E%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fcryptobriefing.com%2Fethereum-service-provider-infura-goes-down-again%2F) outage resulted in metamask experiencing outages and downtime. 

- Centralized RPC node providers reintroduce the problem of trust in a trustless system. We currently have to trust node providers to serve applications with uncompromised data, respect user privacy and ensure the security of data used for analytics.

- Centralized RPC providers have complete control over RPC nodes they provision. This introduces the threats of censorship, providers may decide to censor a particular smart contract, team, blockchain network or dApp. 

| ![Issues with Centralized RPC providers](https://media.discordapp.net/attachments/999832818916020275/1002441832447357018/Dissadvantages_of_centralised_rpc_nodes.png) |
|:--:|
| Issues with Centralized RPC providers, <i>Aishat Akinyemi</i>|

## Decentralized RPC node providers

There is a need for decentralization of RPC node provisioning as it is the gateway to web3. We need decentralized RPC networks designed to solve the challenges and limitations of centralized RPC node providers. 

Currently, one decentralized RPC node provider serves RPC requests at scale—Pocket network. BlockPI [launched its testnet last month](https://medium.com/klaytn/decentralized-rpc-network-blockpi-launches-its-testnet-with-klaytn-edfffa768cac). Ankr published a whitepaper in July 2022, wherein they expressed their plans to decentralise their platform.

### Pocket Network (POKT)

Pocket network is a multi-chain relay protocol made up of nodes that provide decentralized RPC access to
dApps. Pocket network aims to solve the [relay node incentivization problem](https://ethresear.ch/t/incentives-for-running-full-ethereum-nodes/1239), as providers are incentivized to provide developers RPC nodes to relay requests to external blockchains.

| ![Pocket network Utility v0 High Level Overview](https://cdn.hashnode.com/res/hashnode/image/upload/v1664818387929/x_lMbh5Ql.png align="left")
|:--:|
|Pocket network Utility v0 High Level Overview, <i>Pocket</i>|

The protocol uses Tendermint’s  proof-of-stake consensus algorithm, with each pocket node staking 15000
POKT (the network’s native token) to take part in the RPC relay process. Node providers must have DevOps skills and the hardware to set up a Pocket validator node; and (separate) external blockchain RPC node. 

**Pocket network’s RPC relay mechanism**

A single pocket node can have up to 15 associated third-party blockchain full nodes (relay nodes) to which it relays requests. The Pocket Portal is a web app that abstracts interaction with the network away from developers, enabling easy configuration of RPC endpoints. 

To access pocket dRPC nodes, an application developer stakes POKT once-off for perpetual access to a guaranteed maximum volume of relay requests per session. This volume of relay requests is computed based on some variables agreed upon by the Pocket DAO. 

**Proof of relay **

The protocol’s session generation algorithm creates a session with some pseudo-randomly selected nodes that will relay the app’s requests for the timeframe. This random selection ensures that each node has an equal chance at servicing relay requests, irrespective of the amount of its staked POKT.

A node serving requests stores proof-of-relay: a verifiable piece of relay evidence for each successfully-served request. After completing relay requests in a relay session, the service node broadcasts transactions to the network to validate the proofs-of-relay. The chance of a node validating the transactions in a session is proportional to its staked POKT. The validation of proofs-of-relay by the protocol produces a new block and POKT minted. The minted POKT gets distributed to the relevant Pocket nodes. The volume of minted POKT is directly proportional to the number of relays and transaction fees in a block.

There is no direct exchange of POKT between the application and the nodes—this is to ensure that network efforts are on relay requests servicing and block validation and to avoid expending resources on validating on-chain fee payments.

|![Pocket's Proof of relay](https://cdn.hashnode.com/res/hashnode/image/upload/v1664979288105/1X5_lEqNT.png align="left")|
|:--:|
|Pocket's Proof of relay, <i>Aishat Akinyemi</i>|

**Pocket protocol's quality of service**

Pocket ensures the quality of service by rewarding nodes proportional to the number of successful requests they serve. The protocol currently uses off-chain mechanisms to ensure a high quality of service:

- **Sync check** to ensure data consistency by checking that the external blockchain nodes are adequately synced
- **Cherry Picker** service rates nodes' quality of service by their latency and error rate
The quality of service determines the number of relay requests a node receives, thereby incentivizing node providers to provide high-quality service. A provider's stake can be subtracted or burnt to penalize malicious behavior and discourage negligence.

Pocket v2 is in progress with changes proposed, including moving the quality of service measurement on-chain.

## Conclusion

RPC nodes are the gateway to decentralized blockchain networks. The majority of RPC node providers are centralized, with only one decentralized RPC node provider in the market. The access layer centralization undermines web3 decentralization and introduces some information security challenges at the blockchain infrastructure layer level, thus reducing decentralization.

As more innovation, research and efforts go into decentralizing the RPC access layer, there would be improvements in the current decentralized providers like Pocket, and we would see more teams building decentralized RPC infrastructure going live. Decentralizing RPC nodes will benefit web3 developers by making dApps and blockchain applications more decentralized, reliable, fault-tolerant, and censorship-resistant. 

We would also see more centralized RPC providers pursuing RPC decentralization initiatives following Ankr’s steps. The most recent is [Infura's announcement](https://infura.io/resources/network/decentralized-infrastructure-network-early-access-program) on Friday, September 16 that it will launch an open source decentralized protocol for RPC node infrastructure next year. The announcement contained an invitation from Infura to other Web3 infrastructure providers to join its efforts toward building a new decentralized blockchain infrastructure network.

Have you used dRPC endpoints in the past? Do share your thoughts and comments 😀.


