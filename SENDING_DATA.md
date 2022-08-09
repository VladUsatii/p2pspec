# Sending Data

This article explains to how to send data to a peer.

## ⚠️  READ BEFORE FOLLOWING TUTORIAL

* Transaction can be created at ```gemcoin/core/makeTransaction.py```. DO NOT PACK TRANSACTION INTO Hello(0x..). This will be handled by the client! If you do this, your data will be nullified by the peers and you may be blocked.
* Blocks can be mined at ```memory/mining.py```. They are saved as ```saved_block_{blocknum}```. Copy the file contents and use for your block proposal.
* Subprotocol transactions must be coordinated through external governance criteria. These protocols aren't created by Gemcoin and we are not liable for any damage done to your node.

## Transactions

Using ```peers/sendingData.py```, you will be prompted to enter whether you want to send a transaction, a block, or a subprotocol transaction. If you enter ```1```, you are going to be asked to paste a raw transaction before the serialization/protocol encapsulation.

Your transaction should look something like this (make sure it is packed and signed):

```
This is the signed tx (NOT THE ONE YOU INPUT):  {'rawtx': 'b75285dbcba706786c65471faee6713b041eed3cc6d5e48cc0bd648a12f4dd11', 'tx': {'version': '00000014', 'nonce': '0x00', 'workFee': '0000000000000000000000000000000000000000000000000000000000000000', 'timestamp': '0000000000000000000000000000000000000000000000000000000059945280', 'fromAddr': '0x73f5370f2ba7727a95d06f76c738a71ba596235973354bb920f7e14f87326414e4fd05042dfeb70c38f4da4817eb67bb51b16ac37fccd59124ce7aec6db0d1d7', 'toAddr': '0x00000000000000000000000000000', 'value': '0', 'data': '0x00', 'r': '79994795984947641428023677603590509236905213869933334988817171498908136943595', 's': '13801621573404540558912451444514024005886442374940246046295877287662339204493'}}
```

```
This is the raw transaction (ENTER THIS INTO THE PEERSEND PROMPT):
c6c272c5d8917b227261777478223a202262373532383564626362613730363738366336353437316661656536373133623034316565643363633664356534386363306264363438613132663464643131222c20227478223a207b2276657273696f6e223a20223030303030303134222c20226e6f6e6365223a202230783030222c2022776f726b466565223a202230303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030222c202274696d657374616d70223a202230303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030303030303539393435323830222c202266726f6d41646472223a202230783733663533373066326261373732376139356430366637366337333861373162613539363233353937333335346262393230663765313466383733323634313465346664303530343264666562373063333866346461343831376562363762623531623136616333376663636435393132346365376165633664623064316437222c2022746f41646472223a202230783030303030303030303030303030303030303030303030303030303030222c202276616c7565223a202230222c202264617461223a202230783030222c202272223a20223739393934373935393834393437363431343238303233363737363033353930353039323336393035323133383639393333333334393838383137313731343938393038313336393433353935222c202273223a20223133383031363231353733343034353430353538393132343531343434353134303234303035383836343432333734393430323436303436323935383737323837363632333339323034343933227d7d
```

After you enter this and press enter, you will start a peer search and your data will be sent eventually.

Then, your data will be validated and forwarded to more peers. This is a graph to demonstrate how quick word will get out (assuming everyone connects to 5 peers):

```
Round 1: 5 nodes
Round 2: 5**2 nodes
Round 3: 5**3 nodes
Round 4: 5**4 nodes
Round 5: 5**5 nodes
...
Round 10: 5**10 (9765625) nodes
```

## Proposed Blocks

Let's say you just finished mining a block in ```memory/mining.py``` and you saved your packed block to a file. Your filename has a timestamp appended to it. When you run ```./peers/sendingData.py``` and type in ```2```, Gemcoin will look at the block you've mined most recently based on the timestamp. This the block that will be proposed to the nodes.

## Subprotocol Transactions

Undocumented.

---

Written by Vlad Usatii @ gemcoin @ youshould.readproduct.com
