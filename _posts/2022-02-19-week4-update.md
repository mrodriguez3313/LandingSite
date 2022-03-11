---
date: 2022-02-19
title: Week 4 Update for IPNSGoServer Project
categories:
  - Update
author_staff_member: Marco
---

This week I got overly excited to work on implementing republishing and record following. The way I implemented republishing was following the ideas from [this issue](https://github.com/mrodriguez3313/IPNSGoServer/issues/13). I needed to rewrite the code from week 3 to give the functions clear jobs. There still needs work to be done in getting better implementations, but that will happen over time. 

For the time being, the way I was able to get IPNS record republishing done is two ways. Knowing that republishing happens automatically, the only thing that is needed is the key. I created two endpoints, one that accepts an IPFS path and private key (PostKey()). And the other that accepts an IPNS Path and a private key (PutKey()). The first endpoint is important, because it will give someone the ability to publish to IPNS that does not have access to their own node. (browser, "serverless" dapp, mobile device, etc...). The second endpoint is important because someone may want to hand over control of a record they already have. They want someone else to handle the republishing so they can be free to take their node offline as needed (Ipfs on a laptop or mobile device in the future). Finally I created a GetRecord() endpoint that simply accepts an IPNS key (k51foo...) and resolves it. This is helpful for when a user wants to get the content of a record either we have cached already, want us to search the network to resolve a record for them to see, and/or have us update our content for that key.

Now, if people can add their records to be published to our node, then they will also want to delete them. The simplest way to do that would be to delete their key from our node. I created the DeleteKey() endpoint to rm a key from local node. Then republishing would stop as well, because it would not be able to republish the record without the private key. 

IPNS Following is a completely different ball game. I don't need to have the users private key to update content on my node. Half of the solution would be the use of the GetRecord endpoint because it resolves ipns addresses. But that won't give us the opportunity to continuously resolve these records users want us to maintain an uptodate status on. To solve this problem we need a way to periodically call `ipfs name resolve <ipns-key>` on the keys users want us to be uptodate with. So I found a reputable [queue implementation](https://github.com/gammazero/deque) on github by @gammazero from protocol labs that performs O(1) operations from head and tail. The idea is whenever someone sends me a IPNS key, I add it to the queue and run a [cron job implementation in Golang](https://github.com/robfig/cron) that [runs a ipfs-name-resolve command every 2 minutues](https://github.com/mrodriguez3313/IPNSGoServer/blob/f086a54198313ae71fe72f529d68cbb0dfb4e657/server.go#L399) on queue.Head. Then it recycles the record to the back of the queue to be updated again later on. The problem I am handwaiving at this time is the fact that records could be in the queue for an indefinite amount of time considering the queue gets to be extremely large. 

I urge everyone and anyone who reads this that wants to contribute, to not be afriad and spark up conversation/criticism/appreciation. This will help me and the community greatly by display what it is what we want in an IPNS Pinning Service. This way when it is being worked on by someone with a large budget, it will help us get the product we want. 

# Next Week

I will only be available to work on the project Monday&Tuesday as I will be heading out of town. I will be available after that by email, discord(legendofmar#3868), github, twitter (@legendofmar), etc. if needed, but I won't be able to code next week. I won't be back to working on this project until the 5th of March. 

# Future goals

I have planned getting basic deletion from the queue working. I will actually try to create the testing framework now. And I will write up examples and usecases for the project.

Come chat on the IPFS [Community Forum](https://github.com/ipfs/community/discussions/701)!