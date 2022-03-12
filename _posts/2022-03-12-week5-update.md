---
date: 2022-03-12
title: Week 5 Update for IPNSGoServer Project
categories:
  - Update
author_staff_member: Marco
---

As previously mentioned, I was out of town for about the last two weeks. This week I wasn't sure what to focus on because when I got back, I came down with a stomach bug. Thinking of what I could do in a couple days, I decided the best thing would be to set up a website/landing page for the project. 

This was simple as I have created small website before, but for this one I wanted to bring it up in only a couple days and I found the best and easiest way to do that would be to get a free template from one of the many Jekyll template sites out there. The one I went with was Hydra by [CloudCannon](http://cloudcannon.com/). It is opensource under the MIT License as well which I really liked. It is responsive and very easy to work with. 
I had never used Jekyll before so I had to download Ruby and the relevant libraries. The _config file gave me trouble, especially when I went to launch the project under the custom domain name with github pages. I had to delete the URL & Baseurl lines completely so that GH can automatically infer which paths to use.  The project repo reminded me of Python's Flask framework and Frozen Flask, as well as another in the JS ecosystem. 
I had also never used SASS, but I quickly understood how to meneuver around it. Ultimately, it was a good quick experience. 

# Next Week

I will work on getting the word out more. I will work on the website to fix and add some things. I will work on the testing framework for IPNSGoServer and probably refactor code in that endeavor. If I have time I will try to write up an OpenAPI spec, and will force me to think about API keys, security, return values, and more.

Come chat on the IPFS [Community Forum](https://github.com/ipfs/community/discussions/701)!