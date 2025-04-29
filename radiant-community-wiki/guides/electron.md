# Electron

## FIRST USE - ELECTRON WALLET <a href="#first-use-electron-wallet" id="first-use-electron-wallet"></a>

The Electron wallet is recommended for general receiving and sending uses. It uses Electrumx as to connect to the Radiant node.

What you will see in this guide:

* Downloading Wallet
* Seed generation for the wallet.
* Basics for sending and receiving.

### Download the wallet <a href="#download-the-wallet" id="download-the-wallet"></a>

URL: [https://github.com/RadiantBlockchain/electron-radiant/releases](https://github.com/RadiantBlockchain/electron-radiant/releases)

For this guide I recommend the portable version because it does not require installation. This allows you to move it to another pc or make a backup in a simple way.

* **MACOS:** Electron-Radiant-v0.x.x-macosx.dmg
* **WIN PORTABLE:** Electron-Radiant-v0.x.x-portable.exe
* **WIN INSTALL:** Electron-Radiant-v0.x.x-setup.exe
* **LINUX PORTABLE:** Electron-Radiant-v0.x.x-x86\_64.AppImage

![](https://radiant4people.com/guides/electron/first-use/img/01-INSTALLA-WALLET-WINDOWS.png)

The first time it is run, it will be necessary to accept the Windows warning. It is also possible that the antivirus says that it may have a Trojan, but it is a false-positive.

![](https://radiant4people.com/guides/electron/first-use/img/02-FIRST-STEPS.png)

And click in Run anyway

![](https://radiant4people.com/guides/electron/first-use/img/03-FIRST-STEPS.png)

Two icons appear in the installation. The standard version, which is the **Mainnet** and the **Testnet**, which is the testnet network.

![](https://radiant4people.com/guides/electron/first-use/img/04a-MAINNET-TESTNET.png)

The next step is to indicate how to connect the wallet. By default it is correct

![](https://radiant4people.com/guides/electron/first-use/img/04-FIRST-STEPS.png)

Now it is time to create a new wallet and it is necessary to give it a name. To load a backup, it would be necessary to load the file of the wallet

![](https://radiant4people.com/guides/electron/first-use/img/05-FIRST-STEPS.png)

Radiant only works with standard wallets, which is the one to dial. To retrieve a specific private key, it would be option 3

![](https://radiant4people.com/guides/electron/first-use/img/06-FIRST-STEPS.png)

### Create new seed <a href="#create-new-seed" id="create-new-seed"></a>

In the next step we have two important options to choose from. Restore a wallet with the saved words or generate a new one.

In this case we select a new one:

1. Create new seed
2. Restore seed.

![](https://radiant4people.com/guides/electron/first-use/img/07-FIRST-STEPS.png)

The words that appear will be the seed of the new portfolio. It is necessary and obligatory to write them down or copy them to a file. If they are lost, you will lose access to any radiant in the addresses of the portfolio.

**IMPORTANT: MAKE SEVERAL BACKUP COPIES OF THESE WORDS**

![](https://radiant4people.com/guides/electron/first-use/img/08-SAVE-SEED.png)

To ensure that the words are copied correctly, you are asked to enter them all in the following step

![](https://radiant4people.com/guides/electron/first-use/img/09-CHECK-SEED.png)

And the last step is to generate a password that encrypts the wallet.

![](https://radiant4people.com/guides/electron/first-use/img/10-WALLET-PASSWORD.png)

### TAB Options <a href="#tab-options" id="tab-options"></a>

| TAB          | Description                                                           |
| ------------ | --------------------------------------------------------------------- |
| 1. History   | All transactions from all addresses                                   |
| 2. Send      | To send coins to an address                                           |
| 3. Receive   | Address to receive coins and it will always be an unused one.         |
| 4. Addresses | The first 20 seed directions. All are valid for receiving and sending |
| 5. Coins     | The UTXO of each reception                                            |
| 6. Contacts  | Addresses targeted for reuse                                          |

![](https://radiant4people.com/guides/electron/first-use/img/11-ELECTRON-OPTIONS.png)

#### History <a href="#history" id="history"></a>

1. Status of TX.
2. Transaction date.
3. Address label.
4. Amount of RXD of the transaction.
5. Overall balance of the transaction.

![](https://radiant4people.com/guides/electron/first-use/img/12-WALLET-HISTORY.png)

#### Send <a href="#send" id="send"></a>

1. Destination address
2. Name of the address.
3. Send button.
4. Bar to establish network commission.
5. Amount to send

![](https://radiant4people.com/guides/electron/first-use/img/13-WALLET-SEND.png)

If you have entered a password in the wallet, you need to enter it to make a transaction.

![](https://radiant4people.com/guides/electron/first-use/img/13a-WALLET-SEND-PASSWORD.png)

Once everything is filled in correctly, the transaction is displayed.

![](https://radiant4people.com/guides/electron/first-use/img/13B-WALLET-SEND-TX.png)

In history appears this transaction as shown in the image and the transaction will appear in the next block that is generated (about 5 minutes).

1. Coin input
2. Coin output

![](https://radiant4people.com/guides/electron/first-use/img/13C-WALLET-SEND-STATUS.png)

#### Receive <a href="#receive" id="receive"></a>

Address not used to receive new funds

1. his address will always be one that has never received funds.
2. Name to be added to the address

![](https://radiant4people.com/guides/electron/first-use/img/14-WALLET-RECIVE.png)

#### Addresses <a href="#addresses" id="addresses"></a>

The first 20 addresses of the wallet and the amount of coins in each one. In change

![](https://radiant4people.com/guides/electron/first-use/img/15-ADDRESSES.png)

#### Coins <a href="#coins" id="coins"></a>

**Here you can see all received and unspent transactions.**

1. Addresses to receive
2. Number of coins per address

![](https://radiant4people.com/guides/electron/first-use/img/16-WALLET-COIN.png)

If the connectivity button is red, you can fix it by clicking on it and checking the servers to which you are connected.

![](https://radiant4people.com/guides/electron/first-use/img/17-WALLET-NETWORK.png)

In server all servers are loaded and can be added if necessary.

![](https://radiant4people.com/guides/electron/first-use/img/18-WALLET-NETWORK-CONFIGURATION.png)

Here are the servers you can connect to

![](https://radiant4people.com/guides/electron/first-use/img/19-WALLET-NETWORK-STATUS.png)

**ACTUAL SERVERS**

```
electrumx.radiant.ovh 50012
electrumx.radiantexplorer.com 50012
electrumx2.radiantexplorer.com 50012
electrumx.radiantblockchain.org 50012
electrumx.radiant4people.com 50012
```
