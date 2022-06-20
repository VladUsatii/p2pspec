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

### Navigation

To navigate and understand Gemcoin from first principles, we recommend reading the ```blog```. The blog is the collection of updates to the project in order and serve as a "first-principles" repository of changes to the protocol over time. To get an in-depth analysis of the peer-to-peer protocol, the connection "rules," or how blocks, transactions, or headers are packaged and distributed, please consult the blocks folder. In terms of undestanding the rules of the blocks, we recommend reading the "header.md" file first, and then moving on to the blocks.md, and finally the transaction structure/resolution methods.

### HELP

We are actively looking for documentation editors. Please feel free to reach out or contribute.
