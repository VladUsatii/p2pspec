# Block Header Specification

GIP 0 details are below. Please assume changes at any point; any pushes to the Github may invalidate all of the following documentation.

# ```ConstructBlockHeader()```

Every block header, when stored, is currently 352 bytes, or 704 characters. A constructed block header looks like the following (```||``` symbol represents string concatenation):

```version || previous_hash || mix_hash || timestamp || targetEncoded || nonce || num || txHash || uncleRoot```

### Version

Version 20 represents the Genesis Block version and will change every GIP by the following equation:

```
int(20 * e**GIP#)
```

### Previous Hash

A previous hash is the double SHA256 hash of the parent block header. This is used in the mining process to validate that a nonce yields below the target value of the encoded difficulty. Double SHA256 is very useful, as it creates a fixed padding for every hash and removes arbitrary byte lengths.

### Mix Hash

A mix hash is the double SHA256 hash of the child block header (the newest block header). This is used in the mining process to validate that the previous hash combined with the nonce is below the human-readable target.

### Timestamp

The UTC timestamp rounded to the nearest int. It is stored as an 8 byte timestamp.

NOTE: Timestamps in block headers and timestamps in account sharding determinants are two COMPLETELY different things. To see information on sharding, see the sharding folder in the parent directory.

### Target Encoded

This is the current block difficulty target in encoded (hex) format.

The logic behind a decision to accept a block is best summarized theoretically as:

```
newBlock : False
∃! set(encodedblockheader) ^ n
¬newBlock : n ∈ set(encodedblockheader) < targetEncoded
```

In non-math terms:

```
Newblock is always set to False
During mining, there are universally unique guesses of a blockheader appended to a nonce.
To qualify as a newBlock (¬False == True), the nonce in the set must be less in base 10 than the base 10 target.
```

### Nonce

The nonce is the "number only used once." This is the 4-byte digit that is used to verify that a new block's header is below the target.

### Num

The num is the block number. This is a fundamental property of the blockchain. This number is used most often to test block proposals. Discarded blocks are most easily discarded by reading the block number first.

### txHash

This is the root dhash(x) or recursive merkle hash of every transaction included in the block that was withdrawn by priority electricFee from the mempool.

### Uncle Root

If more than one miner finds a valid nonce at the same time and both blocks are propagated through the network, there must be a system such that the block reward is split among the participants. The higher block reward goes to the person who did more computational work, proven by the base-10 repr. of the mixhash.


A deconstructed block header dictionary is structured in the following:

```
{
"version"      : version       uint32_t 4 bytes,
"previous_hash": previous_hash char[32 bytes],
"mix_hash"     : mix_hash      char[32 bytes],
"timestamp"    : timestamp     uint32_t 4 bytes,
"targetEncoded": targetEncoded uint32_t 4 bytes,
"nonce"        : nonce         uint32_t 4 bytes,
"num"          : num           uint32_t 4 bytes,
"txHash"       : txHash        char[32 bytes],
"uncleRoot"    : uncleRoot     char[32 bytes]
}
```

# ```DeconstructBlockHeader()```



# Downloading the chain

To dowwnload only block headers, use a light node client. The projected change in allocation of storage on a machine will change based on the amount of blocks.

```
| Number of blocks     | Storage Space Allocated |
| -------------------- | ----------------------- |
| 0 <= x <= 100        | 40 KB                   |
| 101 <= x <= 1000     | 4 MB                    |
| 1001 <= x <= 10000   | 35 MB                   |
| 10001 <= x <= 100000 | 250 MB (pruning)        |
```

As you can see, a light node requires anywhere from 40 KB of storage (plus a required 250 MB free on the machine), all the way up to 250 MB + 250 MB. At the moment, we require 40 KB, but you may continue to run a light node and ignore the recommendations above. See LICENSE for information on liability.

# 


```

