# About RXD

## What is Radiant?

Radiant (or RXD) is a peer-to-peer electronic cash system. It uses a _blockchain_ to distribute its ledger over a network of independent nodes so that there is no single point of failure, and no central control that might be compromised. It uses a consensus algorithm called _Proof-of-Work_ that allows these independent nodes to approve correct transactions and reject malicious ones.

### Basics <a href="#basics" id="basics"></a>

The _blockchain_ is a data structure that is distributed over a number of independent nodes. It derives its name from the chain of _blocks_ that it uses to store its data. All blocks include a _block header_ with some metadata and the root of a _Merkle tree_ - a special kind of tree that allows quick validation of data. This Merkle tree is then used to store the actual data inside these blocks. To make the chain resistant to manipulation, block headers also include a timestamp and a hash of the previous block.

#### Proof-of-Work <a href="#proof-of-work" id="proof-of-work"></a>

Radiant and many other public blockchains use a consensus algorithm called _Proof-of-Work (PoW)_. This algorithm works by attaching a nonce to every block header and changing this nonce until the hash of the block header matches a certain prefix. This process is called mining, and is attempted by many nodes at the same time, until one of them has found a correct solution. One of the attributes of this algorithm is that mining is very expensive, but other nodes can verify the solution very quickly.

Mining is also the process by which new coins are introduced to the total monetary supply. Miners validate transactions and secure the network, for which they are paid new coins - called the _block reward_ - in a special transaction called a _coinbase_ transaction. The high cost of the mining process attaches a financial risk to incorrectly validating transactions. At the same time the block reward attaches a financial reward to correctly validating transactions. This process ensures that the mutually distrusting nodes can collaborate to validate transactions.

#### Transactions <a href="#transactions" id="transactions"></a>

Radiant transactions are created using chunks of RXD called transaction outputs. When these outputs are available, they are called _Unspent Transaction Outputs (UTXOs)_. UTXOs are locked using a locking script (or `scriptPubKey`) that specifies the conditions to spend the UTXO. When attempting to spend a UTXO, an unlocking script (or `scriptSig`) is provided. These scripts are then executed together and the transaction is only valid if the scripts execute without errors and the resulting value is `TRUE`.

The most used locking/unlocking script pattern is called _Pay-to-Public-Key-Hash (P2PKH)_, where the locking script contains the hash of a public key and expects the unlocking script to contain a public key and transaction signature. The locking script then checks that the provided public key matches the stored hash, and that the transaction signature is valid. This pattern is used in regular Radiant wallets. And the user's balance is simply the sum of all UTXOs that can be spent by the user's public keys.

UTXOs are used as inputs to Radiant transactions and produce new UTXOs as outputs. UTXOs need to be spent in their entirety within a transaction. So whenever the user wishes to use a 10 RXD UTXO to send someone 1 RXD, they need to send 9 RXD back to themselves. Realistically, part of the funds would be reserved for transaction fees as well.

## Smart Contracts <a href="#smart-contracts" id="smart-contracts"></a>

Peer-to-peer electronic cash was the first real use case of blockchain technology. But in recent years, smart contracts have grown in popularity. These smart contracts allow people to use the security that blockchains such as Bitcoin, Radiant and Ethereum offer and apply it to use cases other than cash. Especially Decentralised Finance (DeFi) applications such as [Maker](https://makerdao.com/), [Uniswap](https://uniswap.org/) and [Aave](https://aave.com/) have skyrocketed.

Most smart contract innovation has happened on Ethereum, but other platforms like Bitcoin and Radiant have some support for smart contracts as well. Smart contracts on every platform work differently, and the main differences between smart contracts on Ethereum and Radiant is that smart contracts on Ethereum are stateful, while those on Radiant are stateless.

This means that Ethereum contracts can record and update variables, while the variables in Radiant contracts are immutable.

### Radiant Script <a href="#radiant-script" id="radiant-script"></a>

The locking and unlocking scripts of regular transactions and smart contracts on Radiant are written using Radiant' transaction scripting language, creatively named Script. To avoid ambiguity, it can also be referred to as Bitcoin Script or Radiant Script. Script is a stack based assembly-like language that is intentionally not turing complete as its main use is the validation of programmable money, not general purpose computing.

Script is stateless, meaning it only uses the information contained within the locking and unlocking scripts themselves. This statelessness means that a Script can be deterministically validated on any machine. This gives increased performance and predictability, although it does limit the usefulness of the scripting language.

### Radiant Contracts <a href="#radiant-contracts" id="radiant-contracts"></a>

TODO
