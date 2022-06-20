# Node Persistence Protocol v. 1

There are two types of messages that a peer-to-peer network of inbound and outbound nodes use. ```Checkup()``` persistently "pings" the destination host with useful data, and serves as a tap on the shoulder for TCP to continue its connection. As we all know, TCP closes a "hole" between hosts after a few seconds. On the contrary, the ```Disconnect()``` function pings the destination host and alerts them that they have a 10-second head start to attempt a disconnect before the src node disconnects. This helps nodes running on boomer computers have enough time to panic before an exception is thrown and both nodes are taken offline.

## Hello

Checkup has a generic header:

```
0x00 || version_hash || gemaddr || capabilities [capability, [list_of]] } secret_key
```

- 0x00 represents Checkup's list opcode.
- Version_hash is the git hash of each node. A connection persists if both hashes are the same. Otherwise, it assumes a fork or untrustworthy node.
- Gemcoin address represents the Node identifier (why is the node connecting).
- Capabilities are sub-opcodes that represent functions that the Gem network responds to.
  * Sub-capabilities are descriptions of sub-opcodes. Useful for linked data (indexes, e.g.) on the TCP connection.
- Secret key is the key used for AES communications. Encrypts the header.

Checkup's "subprotocol layer" has a few opcodes.

```
0x00         | RequestAllHeaders
0x01         | RequestNewHeaders
0x02         | RequestBlocks

0x03         | SubprotocolRequest

0x04 [index] | Response
```

## Bye ❌

Disconnect has a generic header. It is way smaller than a Checkup, due to the untrustworthy connection caused by a Disconnect error. This prevents access to the chain from a faulty node. Irregardless, the header is:

```
0x01 || reason
```

- 0x01 represents Disconnect's list opcode.
- Error is the literal error.

The literal error opcodes are as follows:

```
0x00 - Request
0x01 - Useless peer
0x02 - Incorrect version
0x03 - Null received
0x04 - New node introduced (man in the middle attack)
```
