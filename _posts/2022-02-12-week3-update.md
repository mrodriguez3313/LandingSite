---
date: 2022-02-12
title: Week 3 Update for IPNSGoServer Project
categories:
  - Update
author_staff_member: Marco
---

This week I focused on getting the getKey & putKey endpoints working properly. The GET endpoint focused on will generating a key, exporting the key to disk, serving the exported key to client, then deleting all traces of the key from disk and node's keystore. The Put endpoint focused accepting a key file and CID, then importing the key to the node's keystore and publishing IPNS record to IPFS using that key. 

When developing the endpoints, the server.go file was getting too large to sift through. So I took some time to understand the package managing system in Go. To find how to split up the files into relevant features and use variables and functions from the different locations in the other. I updated the README to be easier to understand and reflect the new instructions needed to run the repo.

I added an endpoint to add files to IPFS and it returns the CID. Next, since I needed to grab an uploaded file in more than one endpoint for different reason. I didn't want to duplicate code, and so I made it into its own function called saveFile() that saves the uploaded file to a specific dir.

Ideas for next week spurred out of this question I found on [discuss.ipfs.io](https://discuss.ipfs.io/t/ipns-beyond-the-basics-no-ipns-pinning-service-any-docs-on-this/13424) regarding needing an IPNS pinning service. The main features differentiated by Jorropo were "IPNS Following" and IPNS Republishing. These are features that, in my progress of create this API, I was slowly starting to realize were needed. As I understand it, "IPNS Following" would be a feature of letting a 3rd party service know of what content to download so that they can host the data as well. For example: userA shares CID with userB, thus userB downloads and can now be an additional source to serve the content. This is the same for both IPFS & IPNS. The problem is that IPNS records take MUCH longer to discover than IPFS content. That will have to be a longer discussion... 

To understand IPNS Republishing, we first need to understand IPNS Publishing. To Publish content with IPNS, you need to have the IPFS CID & your private key to sign the record and announce YOU were the one to publish that content and are the true owner. As long as your node is online when the expiration of the record comes along, your node will republish the record to keep it alive and discoverable in the DHT. In other words, to entrust republishing to a 3rd party would require sending the associated private key to them as well. This security risk seems like one people are willing to take, but also far from the web3 paradigm. Regardless I think having it be open source would be a great step towards trust in the platform. But this also means the project will have to store keys (which originally was not the plan) and use them to republish their content. 

One reason for not including republishing in this project, would be to disolve me of that responsibility and thus put the responsibility on the developers to create their own keystores and then they can just make calls to this api to publish via the putKey() endpoint periodically. I could also create a different repo that would serve as a keystore, complete with encryption and other security measures. Then that API would recieve keys use them to publish/republish on this server.

## Next Week

I will be working on returning values over the API, setting status codes, testing endpoints rigorously, setting up test framework, and support for adding directories to IPFS using the API, and setting up basic IPNS following.

Come chat on the IPFS [Community Forum](https://github.com/ipfs/community/discussions/701)!