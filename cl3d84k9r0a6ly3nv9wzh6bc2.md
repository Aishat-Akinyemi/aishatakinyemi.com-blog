## Decentralized Storage Networks — An Explainer.

## Background

Data is important and the technologies built around its transmission and dissemination influence the world at large. From ancient storytellers to writing systems, through to the invention of the Internet and the Web that both revolutionized how society accesses, views, and uses information. 

Decentralization is the crux of the current wave of disruptive information technology innovations. Discussions about data storage in web 3.0 (the decentralized web) frequently refer to decentralized storage networks. What is decentralized storage?  How different is it from traditional cloud storage? How do decentralized storage networks work? And what are the unique applications of, and possible issues with new generation decentralized storage networks?

I will discuss decentralized storage networks and reading this explainer will provide answers to these questions, and hopefully, get you excited and interested in the countless potentials of decentralized storage networks.  

## Traditional Cloud Storage Solutions

Distributed computing and high-speed internet connectivity have enabled the pervasiveness of online (cloud) storage solutions such as Dropbox, Google, Amazon, etc. These solutions are built on distributed server-client networks owned and controlled by individual organizations. The inherent issues with this are risks of censorship, centralization of authority and trust, low fault tolerance, and data security risks.

![1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652975909617/tXAwqcGoh.png align="left")

## Decentralization

Decentralization is the distribution of access and control of a system to the participants, rather than the concentration of power with a central authority or entity.

## Decentralized Storage

A decentralized storage network (DSN a.k.a. decentralized file-sharing network),  is a distributed peer-to-peer (p2p) censorship-resistant network of untrusting nodes cooperating to provide storage capacity. These nodes store chunks of data, each node dedicating disk space, memory, bandwidth, and CPU.  

Decentralized storage systems are designed to be fault-tolerant with intentional data redundancy techniques built in to provide resilience and no single point of failure. Trustless data security and recovery should not be affected by nodes joining or leaving the network. 

One of the peculiarities of this model of data storage is that it shifts resource addressing from a location-centric approach to a content-centric approach.

![2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652976048297/886UKUHQ8.png align="left")

### The generations of decentralized storage networks.

While it has recently garnered much attention DSNs are not a new thing. The first generation of p2p DSNs like Napster, Torrents, etc. were often used for sharing music and video files.  Peers maintained copies of fragments of files on their computers. This fragment is then shared with other node(s) in the network, upon request. Peers could decide to stay online or not, with Torrents, the more a peer provided to the network, the more it enjoyed the download process. 

Lots of work has gone into developing new generation DSNs, built on new and existing technology to provide global, low-latent decentralized distribution of files, websites, applications, and data.

**Important properties of new generation distributed storage systems.**

These are features that distinguish the new generation of distributed storage systems from the first generation DSNs: 

- Economic models to incentivize users to achieve data permanence, and participation.
- Consensus mechanism to prove data storage
- High scalability and robustness.

IPFS, Sia, SafeNetwork, Arweave, 0Chain, Storj, BitTorrent File-System, and Swarm are some prominent examples of new generation DSNs. Many of them have the same underlying technologies applied differently.

In the next section, I discuss the technical concepts common in most DSN implementations.
### Decentralized storage concepts.

Some of the underlying technologies include Torrent, Erasure coding techniques to ensure redundancy, Merkle DAG, Distributed Hash Tables, Blockchain technologies and Consensus mechanisms, etc.

![StorageWorks-01-1.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1652977172874/yVNlxLJLI.jpg align="left") [Technical Overview of DS - Alex Morris](https://weteachblockchain.org/courses/decentralized-storage/2/technical_overview)
- **Data Sharding:** fragmenting a file to be stored in the network into chunks of data. In some DSN, e.g. Safenetwork and Storj, the data is encrypted before it is sharded
- **Content addressing**: As stated earlier, DSN stores and retrieves data based on its contents. This is achieved through hashing algorithms and Merkle Directed Acyclic Graphs (DAG) and Distributed Hash Tables.
    
    The data to be addressed is passed through a hash function to generate its CID. A hash function is (a) deterministic: the same inputs always return the same CID. (b) a one-way function – the input data cannot be derived from its CID. (c) the CID is unique, a slight change in data results in a different CID.    
    
    Since data is always sharded and distributed across peers, we need a data structure to verifiably link chunks of data together as well as represent path information when folders are uploaded. 
    
- **Merkle DAG**: A graph is a data structure used to represent pairwise relationships between objects- nodes. A node with descendants is a root node, and the ones without are called leaf nodes. 
    
    **Directed graph**: has a sense of direction of how nodes are linked — which node contains which nodes. e.g. a folder has a file; a file has data content, not the other way around.
    
    **Acyclic graph:** represents a unidirectional pairwise relationship between nodes e.g. you can only move from a parent node to a child node. 
    
    Merkle DAGs are used to represent hierarchical relationships. Since a CID is unique, DSNs, and other systems like Git, use them to represent relationships between objects with Merkle DAG.
![Merkle DAG.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652976248461/8AxnmYpki.png align="left")

A node’s CID depends on every single one of its descendants in the Merkle DAG. A change in the content of the descendant bubbles up and results in a change in the parent’s CID. These characteristics let us identify data securely and verifiably in a trustless network. 

Merkle DAG lets us link chunks of content, files, folders, and directories together and tracks revisions or changes in contents. A file’s CID would consist of CIDs of the data chunks of its content. A user can then retrieve the whole of the file with the file’s CID.

CID exposes an important feature of DSNs permanence because records of CIDs are kept. Additionally, we can choose to retrieve the sub-content from a DAG with its CID, and embed it in another larger DAG. This allows the deduplication, efficiently storing data by encoding redundant sections as links.

- **Broadcasting:** the chunks of data are distributed in the network for storage by the peers.  No single peer holds the entirety of the data, and data is replicated across peer nodes.
- **Content Look-up:**  DSN uses Distributed Hash Tables (DHT) for content routing. DHT is used in mapping CIDs to peers that have the data (provider records), as well as peer IDs to address at which the peer can be reached. When you request for your file, a node in the network posts a request to its peers most likely to have the data based on the CID lookup in the DHT. 
- **Caching**: The first node to reply supplies the data. The data is then stored in the cache of the requesting node and it can provide it upon request. Nodes can store data that interest them, they may choose to pin the data to persist it. This relates to incentivization.
- **Incentivization:** data is guaranteed to persist in a DSN as long as a node stores it, multiple measures are taken to avoid data loss, including rewarding node operators. Many DSNs have game theoric incentives to encourage participation and discourage malice or negligence. Storage providers enter into storage contracts with users who pay with tokens. Some DSNs such as Filecoin have time-based contracts, while Arweave and Safe have a once-off payment structure. Most DSNs have blockchain-based incentivization mechanisms.
- **Verifiable Content Persistence:** these mechanisms are implemented by networks to verify that data storage claims are being met by nodes and detect a peer’s malicious behaviors.  
They are probabilistic challenges that prove with a high degree of certainty that a provider is fulfilling its storage agreement, well-behaved, and not susceptible to hardware failure. 
    
    Examples of such are Proof-of-space, Proof-of-access, Proof-of-Work, succinct Proof of Random Access, etc.

## New Generation DSNs.

|              | Description                                                                                                                                                                                                     | Incentivization for data persistence                                                 | Consensus and proving mechanisms                                                                                                                      |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| Safe Network | an ongoing DNS project- aiming to provide permanent, storage, and secure storage network. Multiple layers of encryption carried out on data to ensure maximum security                                          | once off payment of Safe Network Tokens.                                             | [Proof of Resource](https://safenetwork.tech/faq/#what-is-proof-of-resource) (similar to Zero Knowledge Proof) and Node Ageing                        |
| Sia          | a DSN where encrypted users’ (aka renters) data are stored at a market-rate determined by the providers and renters. The renters retains ownership of their stored data                                         | Siacoin blockchain                                                                   | [Proof of Work, Proof of Storage](https://siastats.info/sia101)                                                                                       |
| IPFS         | one of the most widely used DNS with many applications and abstractions built on top of it. Persisting your data on IPFS requires a pinning service like Pinnata or designating your own IPFS node for pinning. | Filecoin is a marketplace and blockchain based reward system built by the IPFS team. | [Filecoin uses Proof-of-Replication, and Proof-of-Spacetime](https://filecoin.io/blog/posts/what-sets-us-apart-filecoin-s-proof-system/)              |
| Arweave      | Arweave provides permanent storage by backing data with sustainable and [perpetual endowments](https://www.arweave.org/technology#endowment) similar to traditional economic endowments.                        | Arweave token                                                                        | [Succinct Random Proofs of Access](https://arweave.medium.com/the-arweave-network-is-now-running-succinct-random-proofs-of-access-spora-e2732cbcbb46) |

### Use Cases of Decentralized Storage Networks.

DSNs hold a lot of potentials, and they will facilitate a new iteration of the web, web 3.0. DSNs will be the foundation of a more open, censorship-resistant, secure, and trustless internet. Here are some of the increasingly popular applications of DSNs.

- Blockchain on-chain data storage is expensive, hence decentralized app (dApp) data such as user onboarding data, access management, and identity management, are stored on decentralized storage.
- Website and application hosting on DSN. [Fleek.co](https://fleek.co) provides dApp hosting built on top of IPFS.
- Decentralized cloud storage providers like Storj, Filecoin etc. provide affordable storage competing with traditional cloud storage for enterprise and end users. DSNs aim to offer more performant, affordable, and secure cloud storage solutions — Storj’s storage costs are $11/TB per month and Sia state that the pricing on their network is usually around **$2 per TB per month.**
- Currently, nodes in blockchain networks need to download the entire blockchain to be able to mine/validate blocks of transactions. There is an ongoing effort to employ decentralized storage to allow blockchain data to be shared between mining nodes - Ethereum’s Swarm.
- Identity record management systems store user identification data on DSN. A blockchain registry links the stored id to the user which can be looked up to verify the identity. e.g. [uPort](http://www.uport.me).
- Data permanence in platforms like Arweave will bring about reliable proof of existence of data at a particular point in time and a reliable archival web system.
- Self-authentication. User data ownership would mean that users “plug and play” their data into applications hosted on a DSN. Companies won’t be able to share/sell user data to 3rd parties.

### Issues with DSNs.

Many decentralized storage solutions are still in their infancy. Much research and innovation are still underway and it might take a few years to deliver superior services to centralized cloud solutions. 

- Some DSNs are slow relative to centralized cloud services.
- Current storage offerings are not as simple to use as Dropbox, OneDrive, etc. They often require some technical setup that might discourage a non-tech-savvy user.
- Data impermanence issues on DSNs offerings with time-based storage contracts. Few like Arweave and Safe-Network guarantee permanence with one-off payments.
- Some DSN, e.g. IPFS, do not provide out-of-the-box content encryption, data is stored in public storage network that can be queried by anyone with its CID. This is a good fit in some use cases, but you as a user may have to manually perform encryption when opting for these categories of DSN.
- Many DSN store data in exchange for tokens that rely on blockchain technology. Token price volatility may mean unpredictable storage costs that might make storage cost budgeting difficult. Perhaps we may expect the market to regulate itself, and economies of scale to result in lower prices.

## Conclusion

DSNs are facilitating an iteration of the web that is more secure, persistent, open and robust. This new iteration, web 3.0, fosters the sharing of computing, information and economical resources. DSNs are the foundation on which the future web is being built.

DSNs that will thrive and gain popularity are those that provide resilient, highly available storage rewarding to storage providers and end users. There would be more need for predictable costs of storage in DSNs and we would probably witness more adoption of stable crypto-currencies in these networks.  In the next few years, there would be more projects that abstract away the technicalities from users, such that DSN solutions feel as seamless as the popular cloud storage of today.

As innovations happen and more applications are built on DSNs, the more fitting term would be decentralized computing. There is so much potential and opportunity to build on the decentralized storage networks, perhaps you or I create an amazing project that would bring us closer to this future. 

I would like to hear your thoughts on the aspects of decentralized storage you are most excited about. What new use cases, benefits, and issues come to mind? 

### Want to get involved?

[Arweave will invest up to $100k on your Permaweb Apps](https://arweave.build/),

You can contribute to [IPFS](https://docs.ipfs.io/community/contribute/ways-to-contribute/),
[Get involved in SafeNetwork’s](https://safenetwork.tech/get-involved/) projects,
[Storj offers free 150 GB/month free storage](https://www.storj.io/pricing), and

[Check out NFT Storage for free NFT storage built on  IPFS and  Filecoin.](https://nft.storage/)

**References and more readings**

[Arweave](https://www.arweave.org/)

[BitTorrent File System (BTFS) | Scalable Decentralized File Storage](https://www.bittorrent.com/token/bittorrent-file-system/)

[Consensus Without a Blockchain](https://medium.com/safenetwork/consensus-without-a-blockchain-1dfda94aa435) Maidsafe

[Decentralized Storage | ethereum.org](https://ethereum.org/en/developers/docs/storage/)

[Decentralized Storage | weteachblockchain.org](https://weteachblockchain.org/courses/decentralized-storage/) [Weteachblockchain.org](http://weteachblockchain.org/)

[Distributed Hash Tables](https://docs.ipfs.io/concepts/dht) IPFS

[IPFS](https://ipfs.io/)

[IPFS Whitepaper](https://ipfs.io/ipfs/QmR7GSQM93Cx5eAg6a6yRzNde1FQv7uL6X1o4k7zrJa3LX/ipfs.draft3.pdf) Juan Benet

[IPLD Tutorial | Merkle DAGs: Structuring Data for the Distributed Web | ProtoSchool](https://proto.school/merkle-dags)

[Multiformats Tutorial | Anatomy of a CID | ProtoSchool](https://proto.school/anatomy-of-a-cid)

[SafeNetwork](https://safenetwork.tech/how-it-works/)[](https://www.storj.io/)

[Sia](https://sia.tech/)

[Storj](https://www.storj.io/)

[Swarm](https://blog.ethereum.org/2016/12/15/swarm-alpha-public-pilot-basics-swarm/)

[The Meaning of Decentralization | Vitalik Buterin](https://medium.com/@VitalikButerin/the-meaning-of-decentralization-a0c92b76a274)

[7 decentralized data storage networks compared](https://www.techtarget.com/searchstorage/tip/Comparing-4-decentralized-data-storage-offerings) | Robert Sheldon, Brien Posey


