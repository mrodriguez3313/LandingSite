---
date: 2021-11-25
title: Application Submission for Next-Steps Grant
categories:
  - Roadmap
author_staff_member: Marco
---

I am continuing this project from the Web3 jam project 2021. The idea of NFTs is changing. People are finding use cases for having dynamic metadata. This is possible currently by changing the data off chain then updating the URI in a token. This can be costly and slow because of the need to edit storage on the blockchain. That is why my project aimed to lower those costs. By using IPNS and storing the record/entry on the contract you can update your NFT off-chain. 

My system works by creating an api that accepts requests for private/public keys, then using that to create an IPNS record that gets returned to the user. From there the client will mint an NFT and create the contract with the IPNS record. As long as the user has the ability to customize the URI in which ever easy-to-mint framework or service, they can take advantage of dynamic metadata and even images. 

The goal is to have:
getKeys() -> (returns a private/public key pair
Putkeys(privatekey, IPSFhash) -> (returns IPNS record embeded with public key and ipfs hash)

As this will be open-source, the wish is other companies or people will use this to add to IPNS easily. At the very least, this will serve as a great example on how to isolate and use the IPNS library. Any suggested features for your usecase would be greatly appreciated.


[community application](https://github.com/ipfs/devgrants/issues/123)
