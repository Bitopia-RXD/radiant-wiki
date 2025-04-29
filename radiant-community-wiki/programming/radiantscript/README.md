# RadiantScript

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

### Smart Contracts <a href="#smart-contracts" id="smart-contracts"></a>

Peer-to-peer electronic cash was the first real use case of blockchain technology. But in recent years, smart contracts have grown in popularity. These smart contracts allow people to use the security that blockchains such as Bitcoin, Radiant and Ethereum offer and apply it to use cases other than cash. Especially Decentralised Finance (DeFi) applications such as [Maker](https://makerdao.com/), [Uniswap](https://uniswap.org/) and [Aave](https://aave.com/) have skyrocketed.

Most smart contract innovation has happened on Ethereum, but other platforms like Bitcoin and Radiant have some support for smart contracts as well. Smart contracts on every platform work differently, and the main differences between smart contracts on Ethereum and Radiant is that smart contracts on Ethereum are stateful, while those on Radiant are stateless.

This means that Ethereum contracts can record and update variables, while the variables in Radiant contracts are immutable.

## Radiant Script <a href="#radiant-script" id="radiant-script"></a>

The locking and unlocking scripts of regular transactions and smart contracts on Radiant are written using Radiant' transaction scripting language, creatively named Script. To avoid ambiguity, it can also be referred to as Bitcoin Script or Radiant Script. Script is a stack based assembly-like language that is intentionally not turing complete as its main use is the validation of programmable money, not general purpose computing.

Script is stateless, meaning it only uses the information contained within the locking and unlocking scripts themselves. This statelessness means that a Script can be deterministically validated on any machine. This gives increased performance and predictability, although it does limit the usefulness of the scripting language.

## Radiant Contracts <a href="#radiant-contracts" id="radiant-contracts"></a>

TODO

## What is RadiantScript?

CashScript is a high-level programming language for smart contracts on Radiant. It offers a strong abstraction layer over Radiant' native virtual machine, RadiantScript. Its syntax is based on Ethereum's smart contract language Solidity, but its functionality is very different since smart contracts on Radiant differ greatly from smart contracts on Ethereum. For a detailed comparison of them, refer to the blog post.

If you're interested to see what kind of things can be built with CashScript, you can look at the [Showcase](https://radiant4people.com/docs/showcase) or [Examples](https://radiant4people.com/docs/language/examples). If you just want to dive into CashScript, refer to the [Getting Started page](https://radiant4people.com/docs/basics/getting-started) and other pages in the documentation.

## Command Line Interface

The `cashc` command line interface is used to compile CashScript `.cash` files into `.json` artifact files. These artifacts can be imported and used by the JavaScript SDK or other libraries / applications that use CashScript. For more information on this artifact format refer to [Artifacts](https://radiant4people.com/docs/language/artifacts).

### Installation <a href="#installation" id="installation"></a>

You can use `npm` to install the `cashc` command line tool globally.

```bash
npm install -g cashc
```

### Usage <a href="#usage" id="usage"></a>

The `cashc` CLI tool can be used to compile `.cash` files to JSON artifact files.

```bash
Usage: cashc [options] [source_file]

Options:
  -V, --version        Output the version number.
  -o, --output <path>  Specify a file to output the generated artifact.
  -h, --hex            Compile the contract to hex format rather than a full artifact.
  -A, --asm            Compile the contract to ASM format rather than a full artifact.
  -c, --opcount        Display the number of opcodes in the compiled bytecode.
  -s, --size           Display the size in bytes of the compiled bytecode.
  -?, --help           Display help
```

## Getting Started

### Installing the CashScript compiler <a href="#installing-the-cashscript-compiler" id="installing-the-cashscript-compiler"></a>

The command line CashScript compiler `cashc` can be installed from NPM.

```bash
npm install -g cashc
```

### Installing the JavaScript SDK <a href="#installing-the-javascript-sdk" id="installing-the-javascript-sdk"></a>

The JavaScript SDK can be installed into your project with NPM.

```bash
npm install cashscript
```

:::caution CashScript only offers a JavaScript SDK, but CashScript contracts can be integrated into other languages as well. Because there are no ready-to-use SDKs available for them, this is considered advanced usage, and it is recommended to use the JavaScript SDK. :::

### Writing your first smart contract <a href="#writing-your-first-smart-contract" id="writing-your-first-smart-contract"></a>

There are some examples available on the [Examples page](https://radiant4people.com/docs/language/examples), that can be used to take inspiration from. Further examples of the JavaScript integration can be found on [GitHub](https://github.com/Bitcoin-com/cashscript/tree/master/examples). A simple example is included below.

```solidity
pragma cashscript ^0.7.0;

contract TransferWithTimeout(pubkey sender, pubkey recipient, int timeout) {
    // Allow the recipient to claim their received money
    function transfer(sig recipientSig) {
        require(checkSig(recipientSig, recipient));
    }

    // Allow the sender to reclaim their sent money after the timeout is reached
    function timeout(sig senderSig) {
        require(checkSig(senderSig, sender));
        require(tx.time >= timeout);
    }
}
```

:::tip Read more about the CashScript language syntax in the [Language Description](https://radiant4people.com/docs/language/contracts). :::

### Integrating into JavaScript <a href="#integrating-into-javascript" id="integrating-into-javascript"></a>

While more detailed examples are available on GitHub, we show an integration of the `TransferWithTimeout` contract in a JavaScript project.

After compiling the contract file to an artifact JSON with cashc, it can be imported into the CashScript SDK.

```bash
cashc ./transfer_with_timeout.cash --output ./transfer_with_timeout.json
```

```javascript
const { ElectrumNetworkProvider, Contract, SignatureTemplate } = require('cashscript');
const { alice, bob, alicePk, bobPk } = require('./keys');

async function run() {
  // Import the TransferWithTimeout JSON artifact
  const artifact = require('./transfer_with_timeout.json');

  // Initialise a network provider for network operations
  const provider = new ElectrumNetworkProvider('mainnet');

  // Instantiate a new TransferWithTimeout contract
  const contract = new Contract(artifact, [alicePk, bobPk, 600000], provider);

  // Call the transfer function with Bob's signature
  // i.e. Bob claims the money that Alice has sent him
  const transferDetails = await contract.functions
    .transfer(new SignatureTemplate(bob))
    .to('bitcoincash:qrhea03074073ff3zv9whh0nggxc7k03ssh8jv9mkx', 10000)
    .send();
  console.log(transferDetails);

  // Call the timeout function with Alice's signature
  // i.e. Alice recovers the money that Bob has not claimed
  const timeoutDetails = await contract.functions
    .timeout(new SignatureTemplate(alice))
    .to('bitcoincash:qqeht8vnwag20yv8dvtcrd4ujx09fwxwsqqqw93w88', 10000)
    .send();
  console.log(timeoutDetails);
}
```

**Tip:** Read more about the JavaScript SDK in the [SDK documentation](https://radiant4people.com/docs/sdk/instantiation).
