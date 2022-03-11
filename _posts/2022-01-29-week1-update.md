---
date: 2022-01-29
title: Week 1 Update for IPNSGoServer Project
categories:
  - Update
author_staff_member: Marco
---


Here is my week 1 update as per my IPFS grant! This week I switched from working straight onto the Get/Put endpoints, to seeing if I can get the basic functionality working. I made a branch called testFunc where I am working currently and current progress is focused on the function called testFunctions(). I got as far as generating keys and creating an entry with those keys. I am having trouble publishing the entry. The goal for next week is to get publishing working properly. Then start working on refactoring code to create clear and specific functions. From there I will start working on getting basic GET functionality working.

Problems I ran into this week limiting progress were: 
- Learning how to code in Golang
- Going through docs and understanding how things tie in together
- How to nit-pick certain code bits to use in my code
- How to programmatically generate keys in Go
   - How can I access local node keystore and grab one specific key from it?
- How to publish newly created IPNS entry, programmatically, in Go.
   - How do I grab the key to sign Entry?

I ran in to various errors at the publishing phase: 
1. panic: name/publish: can't replace a newer value with an older value
2. name/publish: no key by the given name or PeerID was found

Here are some questions I asked this week. [discuss.ipfs.io](https://discuss.ipfs.io/t/publish-to-ipns-in-go/13269)

The resources that I found, that had the same error messages, didn’t seem related to my problem. And I think it’s a matter of just not passing in the correct items into the Publish function or handling the keys properly. But any advice would be greatly appreciated!

Come chat on the IPFS [Community Forum](https://github.com/ipfs/community/discussions/701)!