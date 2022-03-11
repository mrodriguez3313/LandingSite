---
date: 2022-02-04
title: Week 2 Update for IPNSGoServer Project
categories:
  - Update
author_staff_member: Marco
---
This week was focused on getting key generation and publishing working properly. I was on the verge of figuring it out last week and that mission was completed this week [solution 1](https://discuss.ipfs.io/t/ipfs-repo-lock-someone-else-has-the-lock/13350/3). It was not the sophisticated solution I had hoped for, but I pivoted to using the api commands. Then I refactored my code to be better suited for scaling up.

The second problem I tackled this week was working on getting keys to and from users. For this I looked into the key export and import functions that are part of the keystore library. The problem I ran into is that they are not implemented in the shell. I ran into the "command not found" error and so I resulted to doing things the hacky way [solution 2](https://discuss.ipfs.io/t/panic-key-export-command-not-found/13358/2). Doing things this way I could take advantage of the api command as if I was running it from the CLI. I believe, any other way, I would have continued running into "command not found" error or "someone else has lock" error from the daemon holding the ipfs repo hostage.

Next step is to finally implement the API so that I can get keys exported to the user. This will be the GetKey() endpoint and thus be able to request a key and get it returned to user as a file through the `ipfs key gen <name> & ipfs key export <name>` api commands. This is helpful considering that this will enable users from web browsers, backend applications, mobile devices, etc... to start harnessing the power of IPNS!

As always, I am looking for contributors. You can find me in the IPFS discord (legendofmar#3868), Twitter (legendofmar), or on github! 

Come chat on the IPFS [Community Forum](https://github.com/ipfs/community/discussions/701)!