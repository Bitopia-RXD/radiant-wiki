---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# FAQs

## What is Radiant? <a href="#what-is-radiant" id="what-is-radiant"></a>

Radiant is a peer-to-peer programmable digital asset system, derived from a fork of the Bitcoin Cash (BCH) genesis block. It introduces new Opcodes that enable Turing completeness and mathematical induction proofs, effectively addressing the "back to genesis" problem. This innovative design combines the performance and parallelism advantages of an Unspent Transaction Output (UTXO) blockchain with the contract capabilities found in Ethereum-based blockchains, specifically the Ethereum Virtual Machine (EVM).

* Powered by Proof of Work (PoW)
* Supports Smart Contracts
* Launched fairly
* Utilizes a robust hashing algorithm, SHA512256d
* Implements the ASERT DAA (Difficulty Adjustment Algorithm)
* Genesis Date: June 20, 2022, 02:42:50 GMT+0000
* Genesis Hash: [0000000065d8ed5d8be28d6876b3ffb660ac2a6c0ca59e437e1f7a6f4e003fb4](https://radiantexplorer.com/block/0000000065d8ed5d8be28d6876b3ffb660ac2a6c0ca59e437e1f7a6f4e003fb4)
* Block Time: 300 seconds (5 minutes)
* Halving: Every 2 years (every 210,000 blocks)
* Subsidy Emission: 50,000 per block (Now 25,000 per block)
* Total Coins: 21 billion, divisible into 8 decimal places (100 million photons per RXD)

## What makes Radiant stand out from other blockchain platforms?

Radiant stands out for several reasons:

* Induction Proofs that solve the "back-to-genesis" problem without the need for indexers.
* Account Emulation, enabling Ethereum Virtual Machine (EVM)-like applications.
* A Turing-complete scripting language known as RadiantScript.
* The "0-conf" feature for instant transactions.
* A Split Node System designed for scalability.

## How was Radiant fairly launched? <a href="#how-was-radiant-fairly-launched" id="how-was-radiant-fairly-launched"></a>

Radiant was launched as a 100% PoW blockchain, ready for use, without any involvement of investors, ICOs, premining, or coin allocations. Mining guides and instructions, including how to mine with rented hash power, were publicly released by Atoshi, Radiant's developer, ensuring that everyone had equal access to RXD coins from day one.

## What is Radiant ethos? Is Radiant considered an investment? <a href="#what-is-radiant-ethos-is-radiant-considered-an-investment" id="what-is-radiant-ethos-is-radiant-considered-an-investment"></a>

Radiant aims to be a scalable and flexible blockchain technology, not primarily designed for investment purposes or generating profits from RXD coin holdings. Similar to Bitcoin, which was created as a peer-to-peer electronic cash system, Radiant was designed as a peer-to-peer programmable digital asset system. While you can still acquire RXD coins from exchanges, it's essential to understand that there are no guarantees of further development. Always perform your research (DYOR) and exercise caution when considering any investment.

## Why is it a fork from BCH? <a href="#why-is-it-a-fork-from-bch" id="why-is-it-a-fork-from-bch"></a>

BTC civil wars divided blockchain enthusiasts into small-block and big-block proponents. In BTC, small-blocks won and big-block proponents forked it to create BCH. BCH still ended deviating from what BTC was supposed to be based on what is stated in the Bitcoin Whitepaper.

Another fork (BSV) was made, aiming to make it as close as possible to the original BTC proposed by Satoshi Nakamoto. This version of Bitcoin is still far from perfect as it has to rely on third party indexers to function properly. Additionally, its associations with an individual who claims to be Satoshi Nakamoto who has initiated legal actions against some blockchain projects, raised concerns about potential legal challenges.

This made BCH a more favorable choice for Radiant's development.

## What’s special about SHA512256d? <a href="#whats-special-about-sha512256d" id="whats-special-about-sha512256d"></a>

SHA512256d is a hashing algorithm that applies SHA-512 and truncates its 512-bit output to 256 bits. While SHA-256 is already secure, Radiant selected SHA512256d to provide a robust, battle-tested foundation for a blockchain designed for ASIC compatibility. By leveraging SHA-512's efficient 64-bit operations and widespread hardware support, SHA512256d optimizes performance on 64-bit processors, enhancing ASIC development and integration. This approach delivers efficient mining and scalable blockchain validation, outperforming more computationally demanding algorithms.

## When will ASICs for Radiant mining be available? <a href="#when-will-asics-for-radiant-mining-be-available" id="when-will-asics-for-radiant-mining-be-available"></a>

Radiant was specifically designed to transition from GPU mining to ASIC mining for enhanced scalability and efficiency. The chosen SHA512/256d algorithm simplifies ASIC manufacturing.

Radiant now has ASIC miners publically available on the market as of September 5th 2024. The first manufacturer to announce a Radiant compatible SHA512/256d ASIC miner was DragonBall Miner, with the [A11 Dual ASIC Miner](https://dragonballminer.com/en/product/dragonball-miner-a11/).

ICERIVER was the second manufacturer to release an ASIC miner for Radiant, with the [ICERIVER RXD RX0](https://www.iceriver.io/product/iceriver-rxd-rx0/).

## Why is the block time 5 minutes? <a href="#why-is-the-block-time-5-minutes" id="why-is-the-block-time-5-minutes"></a>

A 5-minute block time offers faster transaction confirmations compared to Bitcoin (BTC) while maintaining stability and security by minimizing orphan blocks. With block sizes of up to 256MB and the potential for even larger blocks, selecting the right block time is essential. In Radiant, the block time, thanks to its features, does not directly limit transactions per second or transaction speed.

## What is Radiant's total supply and emission schedule? <a href="#what-are-the-benefits-of-radiants-tokenomics" id="what-are-the-benefits-of-radiants-tokenomics"></a>

Radiant has a total maximum supply of 21 billion RXD, with a Proof of Work emission schedule emitting block rewards to miners every 5 minutes (300 seconds), with block rewards halving every 2 years.

Beginning with its Genesis Block on the 20th of June 2022, Radiant's initial block reward was 50,000 RXD per block, and Radiant's first halving event occurred on the 19th April 2024, halving to 25,000 RXD.

The next halving event for Radiant will occur around the middle of April 2026, reducing the block rewards to 12,500 RXD per block.

| Year | Halving | Block Reward | Block Height | Circulating Supply |
| ---- | ------- | ------------ | ------------ | ------------------ |
| 2022 | Genesis | 50,000 RXD   | 0            | 0                  |
| 2024 | 1st     | 25,000 RXD   | 210,000      | 10,500,000,000 RXD |
| 2026 | 2nd     | 12,500 RXD   | 420,000      | 15,750,000,000 RXD |
| 2028 | 3rd     | 6,250 RXD    | 630,000      | 18,375,000,000 RXD |
| 2030 | 4th     | 3,125 RXD    | 840,000      | 19,687,500,000 RXD |
| 2032 | 5th     | 1,552.5 RXD  | 1,050,000    | 20,343,750,000 RXD |
| 2034 | 6th     | 781.25 RXD   | 1,260,000    | 20,671,875,000 RXD |
| 2036 | 7th     | 390.625 RXD  | 1,470,000    | 20,835,937,500 RXD |
| 2038 | 8th     | 195.3125 RXD | 1,680,000    | 20,917,968,750 RXD |

Radiant will effectively have 0 block rewards within the year 2108, when the block reward falls below 1 photon (1/100,000,000 RXD) after the 43rd halving.

## How many transactions per second can Radiant achieve?  <a href="#what-is-the-back-to-genesis-problem" id="what-is-the-back-to-genesis-problem"></a>

With the current block size of 256MB, Radiant is capable of doing 4,000 TPS (Transaction Per Second). If needed, miners can optimize in the future to scale linearly. The Radiant Blockchain is designed to scale towards 500,000+ TPS.

## What are the benefits of Radiant's tokenomics?

Radiant's tokenomics, with a 21 billion coin supply and 8 decimal places (100 million photons per RXD coin), positions it well for tokenizing digital and real-world assets while ensuring ample availability of RXD for both micro and macro transactions. The block time, block reward, and bi-yearly halvings serve as incentives attractive to miners and investors alike.

## What is the Back-To-Genesis problem? <a href="#what-is-the-back-to-genesis-problem" id="what-is-the-back-to-genesis-problem"></a>

In blockchain terms, the "back-to-genesis" problem refers to the ability to validate that all coins, transactions, and digital assets can be traced back to the genesis block. Radiant successfully solves this problem, enabling it to operate as a truly decentralized and permissionless digital asset system without relying on external third-party indexers.

## What does Turing Complete mean and why have it? <a href="#what-does-turing-complete-mean-and-why-have-it" id="what-does-turing-complete-mean-and-why-have-it"></a>

Turing completeness, in the context of a programming language, signifies that there are no limits to the types of computations that can be performed. Radiant's Turing completeness allows for highly flexible smart contract capabilities similar to those of Ethereum but without the scalability issues and high gas costs. This feature makes Radiant a unique and groundbreaking blockchain, capable of supporting a wide range of cryptocurrency and blockchain technology use cases.

### _**How is Radiant protected against attacks that harness turing completeness if it doesn't have a gas system like ETH?**_

Radiant, while Turing complete, does not incorporate loops. Loops must be unrolled to the maximum number of iterations required. This design simplifies and secures script execution, allowing fees to be calculated per byte. This discourages malicious actors from creating overly complex or inefficient scripts, as they would incur higher fees.

## What are 0conf transactions and are they safe? <a href="#what-are-0conf-transactions-and-are-they-safe" id="what-are-0conf-transactions-and-are-they-safe"></a>

A 0-conf transaction is one broadcasted to the blockchain but not yet included in a block (i.e., 5 minutes have not passed). These transactions are useful and safe for microtransactions. Thanks to induction proofs, recipients of 0-conf transactions can be confident that the sender indeed owns the funds being transferred. However, there is a minor risk of double-spending in such transactions.

For small transactions, the potential reward for attempting a double-spending attack is typically much lower than the cost of acquiring mining hardware, electricity, and competing with the network's hash rate. In practice, it's not economically rational for an attacker to invest significant resources in double-spending small transactions.

For larger transactions, it's advisable to wait for inclusion in a block, which provides increasing security with each additional block confirmation.

## Does Radiant have Replace-By-Fee (RBF)?

Radiant does not have RBF implemented. Radiant's decision to exclude Replace-by-Fee is a strategic choice that enhances transaction security, reduces double spend risks, and simplifies the user experience.

By prioritizing transaction finality and promoting responsible fee management, Radiant fosters a more secure and reliable blockchain environment.

This approach aligns with its commitment to maintaining a robust, miner-driven network that users can trust for fast, low cost, and dependable transactions.

### _**The Benefits of Not Having Replace-by-Fee (RBF) in Radiant, RXD**_

In the world of blockchains, transaction security and network reliability are paramount. One feature that often sparks debate is Replace-by-Fee (RBF) vs, First In First Out (FIFO). While some blockchains implement RBF to allow users to replace a pending transaction with a new one that includes a higher fee, Radiant has opted not to include this feature.

Here's why this decision benefits the Radiant network and its users:

#### **1. Enhanced Transaction Finality**

By not supporting RBF, Radiant ensures a higher degree of transaction finality once a transaction is broadcast to the network. This means that once a transaction is sent, it's committed to the network's mempool, reducing the risk of the transaction being replaced or tampered with. This provides more confidence to recipients, particularly in situations where quick transaction acknowledgment is essential.

#### **2. Reduced Double Spend Risks**

RBF can be exploited for double spend attacks, especially in low-confirmation transactions. For instance, a user could broadcast a low-fee transaction to one party, then replace it with a higher-fee transaction to a different party, attempting to defraud the first recipient. To mitigate these risks, many businesses and users wait for several confirmations before considering a transaction final, especially for larger amounts. Radiant's decision to exclude RBF minimizes this risk, making it safer for merchants and users to accept zero or low-confirmation transactions without the fear of an attack.

#### **3. Simplicity and Predictability**

Excluding RBF simplifies the transaction process for users and developers. With RBF, users have to be cautious about transaction replaceability, potentially leading to confusion or errors. Radiant's straightforward approach means that once a transaction is sent, users can have confidence that it won't be replaced, leading to a more predictable transaction experience.

#### **4. Encouraging Responsible Fee Management**

Without RBF, users are encouraged to consider transaction fees carefully before broadcasting. This helps prevent network congestion caused by users continually adjusting fees to prioritize their transactions. It fosters a more balanced network usage where users evaluate the urgency of their transactions in relation to current network conditions, promoting a healthier fee market. Miners can still choose to process higher fee transactions at will, but the volume and speed of putting more transactions in a block is more valuable and hence important in a scalable network.

#### **5. Aligning with Proof of Work Security**

Radiant's Proof of Work consensus mechanism relies on the security provided by miners who validate and add transactions to the blockchain. By not having RBF, Radiant reinforces the trust in its PoW system, ensuring that transactions are treated as irreversible once included in a block. This aligns with the core principles of PoW, where the longest chain and the work behind it determine the network's state.

#### **6. Back to Satoshi's original ideals**

Bitcoin originally operated on a First-In-First-Out (FIFO) basis for transaction processing within the mempool. This means that transactions were typically processed in the order they were received by the network, regardless of the transaction fee. Miners would include the earliest transactions in the next block, provided they met the standard criteria for validity and size. Networks like Radiant that focus on true scalability by having adequate block space and faster block production will not suffer the same fate as size constrained and artificially limited networks. So the need for something like RBF is negated.

## How does the Split Node System work? <a href="#how-does-the-split-node-system-work" id="how-does-the-split-node-system-work"></a>

Radiant employs a Split Node System to accommodate its big-block design and scalability needs. Nodes in Radiant can operate in three different ways:

* **Mining Nodes:** Lightweight, non-resource-intensive nodes dedicated to mining.
* **Agent Nodes:** Contain essential information required for specific decentralized applications (dApps) and smart contracts.
* **Archival Nodes:** Store the complete blockchain for comprehensive data access.

## Who created Radiant? <a href="#who-created-radiant" id="who-created-radiant"></a>

Radiant was bootstrapped and introduced to the world by an individual or group of individuals using the pseudonym "Atoshi." Similar to the anonymous creation of Bitcoin by Satoshi Nakamoto, Atoshi delivered a fully functional product without making any promises or guarantees, allowing the community to shape its future.

## How to mine Radiant? <a href="#how-to-mine-radiant" id="how-to-mine-radiant"></a>

A step-by-step guide on [how to mine RXD with an ASIC miner](https://pool.kryptex.com/articles/how-to-mine-radiant-en).

Radiant's initial GPU mining guide when it was first launched can be found on [GitHub](https://github.com/RadiantBlockchain/rad-bfgminer/blob/master/MINING_RAD_GUIDE.md).

## How to run a Radiant node? <a href="#how-to-run-a-radiant-node" id="how-to-run-a-radiant-node"></a>

Check the Radiant node deployment guides

* [Compile Node](https://radiant4people.com/guides/node/compile/)
* [Run Node with Docker](https://radiant4people.com/guides/docker/radiant-node-guide/)
* [Run Node on Flux](https://radiant-community.medium.com/host-your-electrumx-radiant-node-via-the-flux-marketplace-ecf2388832d6)

### Is there any reward for running a node? <a href="#is-there-any-reward-for-running-a-node" id="is-there-any-reward-for-running-a-node"></a>

No, Radiant is a 100% PoW Blockchain. The only way to get RXD is through mining.

## What wallets are compatible with Radiant? <a href="#what-wallets-are-compatible-with-radiant" id="what-wallets-are-compatible-with-radiant"></a>

You can access your RXD through:

### Software wallets <a href="#software-wallets" id="software-wallets"></a>

You can access your RXD through:

**Software**

* [Electron Radiant Wallet:](https://github.com/RadiantBlockchain/electron-radiant/releases/tag/v0.1.4) Open source desktop wallet based off the popular BTC wallet upgraded for RXD.
* [ChainBow Wallet:](https://chainbow.io/) Mobile and desktop wallet compatible with 0-conf transactions.
* [Photonic Wallet:](https://photonic.radiant4people.com/) A multi platform wallet developed by Radiant community developers, compatible with digital asset minting (Glyph Protocol assets).
* [Photonic Wallet - Extension:](https://chromewebstore.google.com/detail/photonic-wallet/ldagidbelgfoonfhbggfgmlhaccfeepb?pli=1) Install via the Chrome Web Store.

**Hardware**

* [Tangem Wallet:](https://tangem.com/en/pricing/?promocode=RADIANT/en/) Slim as a bank card, secure as a bank vault.

## What developer tooling is available on Radiant?

The current toolbox available to help developers build on Radiant is:

* [RadiantJS:](https://github.com/chainbow/radiantjs) Radiant JavaScript Library.
* [RXD.WASM/RXD-RS:](https://github.com/RadiantBlockchain-Community/rxd-wasm) Rust/WASM Library to interact with Radiant.
* [RadiantScript:](https://github.com/RadiantBlockchain-Community/radiantscript) Fork of CashScript with support for Radiant Opcodes to create complex smart contracts.
* [Glyph Protocol:](https://github.com/RadiantBlockchain-Community/glyph-miner?tab=readme-ov-file#protocol) Create Fungible Tokens, Non-Fungible Tokens, or Smart Contracts by utilizing digital signatures on Photons, the sub-units of Radiant's coin, RXD.
* [Photonic Wallet:](https://github.com/RadiantBlockchain-Community/photonic-wallet?tab=readme-ov-file#introduction) A non-custodial wallet for minting and transferring tokens, following the Glyphs Protocol. The code runs completely client side and only requires a connection to an ElectrumX server.
* [Photonic Wallet - Extension:](https://chromewebstore.google.com/detail/photonic-wallet/ldagidbelgfoonfhbggfgmlhaccfeepb?pli=1) Utilize the Photonic Wallet extension available at the Chrome Web Store.
* [Muon Pay SDK:](https://github.com/RadiantRanger42/MuonPaySDK) A powerful and easy-to-integrate solution for merchants looking to accept payments on the Radiant (RXD) blockchain.
* [Radiant Server Setup Guide:](https://github.com/telostia/radiant-server-easy-setup) Easy to follow guide on how to setup and run a Radiant Node and ElectrumX Server.
* [Glyphs Protocol Tech Guide:](https://radiantblockchain.org/glyphs-protocol-guide.html) Learn the technical details on how the Glyphs Protocol works on Radiant.
