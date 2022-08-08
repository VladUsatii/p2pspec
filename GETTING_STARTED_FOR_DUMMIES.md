# An Introduction to Gemcoin

This quick article will simplify the process of joining the Web3 network. It will take you a maximum of 5 minutes to set up.

Questions or concerns? Please contact us or submit a pull request!

## Getting Started

### Clone the repository

```
git clone https://www.github.com/VladUsatii/gemcoin.git
```

### Creating your keys 🔑

To create a private key (your secret key), public key (your publicly-shared key), and "public address," (Gemcoin doesn't really use a public address -- we use a modified public key as an address, and merkle (combined) hashes for contract addresses) go to the Gemcoin folder:

```
cd gemcoin
```

Give permissions to the ```add_key``` file:

```
chmod +x add_key_NEW.py
```

Run it:

```
./add_key_NEW.py
```

And your key is generated! It isn't "securely generated," but it is good enough. If you want to generate your own key pair in a "more secret" way, make sure to use the SECP256k1 curve on ECDSA. Make sure to generate a ```SigningKey``` and ```VerifyingKey```. Convert them to ```hex().```

### Run the blockchain ⚙️

To "set up" the blockchain (caches, platform checks, sync to other users), go to the ```peers``` folder:

```
cd peers
```

Rinse and repeat:

```
chmod +x main.py
./main.py
```

And wait.

You can leave this system running as long as you want. After syncing the chain to your computer, you will begin verifying transactions, adding them to your mempool, and, if you want, you can mine coins..

## Mining Coins

### What are the units of coins?

| Name  | Unit |
| ------------- |:-------------:|
| Shard      | 10<sup>-14</sup> gems    |
| Kiloshard      | 10<sup>-11</sup> gems   |
| Megashard      | 10<sup>-8</sup> gems     |
| Gigashard | 10<sup>-5</sup> gems |
| Gem | 1 gem |
| Electricity | 10 gems |

### Mining? What?

To mine a shard (the smallest unit of gems), you can volunteer to expend a certain amount of energy to guess SHA256 hashes that, once converted to base-10, are below the previous nonce of the newest block. Once your SHA hash is below the target, you are rewarded with the right to enter transactions from your mempool.

Gemcoin is aware of MEV (miner extractable value), but it doesn't pose an existential risk to our system because of our use of democratic mining (will be implemented soon, as of Mon Jun 20, 2022).

To mine a coin, navigate to the Gemcoin folder and do the following:

```
cd memory
chmod +x mining.py
./mining.py
```

And you will start mining coins. If you want, you can build your own miner, but it must adhere to the standards that are reflected in our code's documentation. You can find this documentation in the gemcoin docs repository.

## Sending Transactions

To send a transaction, you must first know the process by which a transaction is sent:

```
1) You construct a transaction from the Gemcoin template
2) You must sign the raw transaction with your private key using one of our built-in functions
3) You must locally validate the signed transaction to confirm that the private key was used to sign the 'fromAddr' field (your public key).
```

To add the transaction to the Gemcoin Omniscient Network Explorer (GONE), navigate to the ```peers``` directory. From here, add your transaction to the ```node_message()``` function as a response method. Make sure to construct the ```send_to_node()``` function with your signed transaction. Place it in the body of the response handler.

**EDIT: We will streamline this process in the near future.**

### Alternate Method to Sending Proposals to Nodes

In ```peers```, you can also use the ```sendingData.py``` file to add a file to send to nodes. Run it through:

```
chmod +x sendingData.py
./sendingData.py
```

----

Written by Vlad Usatii @ gem & youshould.readproduct.com
