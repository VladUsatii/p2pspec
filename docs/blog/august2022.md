# August 2022

I haven't written a blog for a while, but a very large portion of the project has been completed.

A few changes:

* We created a cryptography library for AES, signatures, and, in the future, zero-knowledge proofs.
* We created a working mining system and file format.
* We created a peer send layer (the place you paste data to send to a peer).
* We now have three formats that data can be in:
  - Raw data (JSON)
    * This data can't be sent. It is made for being looked at.
  - Packed data (bytes)
    * This data is how most of your data should stay. This is how you paste it into our peer send layer and how data is stored in your computer.
  - Encapsulated data (Hello(Opcode, data) or Bye(reason))
    * This is the lowest-level serialization of data. This is how data is sent between peers, but not how it is stored or verified.

* We also created node synchronization tests, added the ability for users to create subprotocols, and we started working on the spin programming language for sending "contracts" to users through transactions.
