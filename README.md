# p2pspec

This is the documentation and spec document source.

You can view anything from my blog posts about the development process to the functioning of the protocol in general. The Gemcoin team tries to make everything easy to read for beginners, so if anything isn't explained well enough, please shoot us a pull request or open an issue to discuss it.

### Breakdown

As of right now, this is the tree layout of the spec folder titled "docs":

```
.
├── ERRORS.md
├── FEE.md
├── GIP1.md
├── PEERS.md
├── PERSISTENCE.md
├── WIREPROTOCOL.md
├── blocks
│   └── HEADER.md
├── blog
│   ├── december2021.md
│   └── january2021.md
└── electricityFormalSpec.png

2 directories, 10 files
```

### TODO:

Write a formal specification for the wire protocol. Right now, we have two different types of wire protocols and it is hard to program without picking the best alternative.
