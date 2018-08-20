---
layout: post
title:      "Polishing Up My Portfolio"
date:       2018-08-20 05:26:39 +0000
permalink:  polishing_up_my_portfolio
---


This week I focused primarily on my portfolio site. I have it more or less styled the way I want, so now I am working on getting the content a bit more fleshed out. I got all of the problems with routing figured out, and I have started migrating my blog posts over to the new site. I've done that for several reasons: I don't want to link to an external blog, and I want my blog to benefit from the same styles as my portfolio. Granted, for the time being everything is hard-coded. I took all my posts and re-created them in separate components which I then added to my repo. It doesn't exactly feel like the right way to do it, but for now it's the best solution I have. At least until I can figure out...

## PERN - What's It All About?
I've heard of MERN and MEAN, but I haven't as yet really taken any time to explore those odd-sounding things. Then, this week while I was debating whether it would make sense to add any complexity to my portfolio site by adding some back-end functionality, I came across **PERN**: ***PostgreSQL + Express.js + React.js + Node.js***. You see, I know how to hook up a Rails API to a React app. But it just seemed like a really heavy-handed solution to my problem. I know that eventually my portfolio will grow beyond the few projects I have in it so far, and my blog will contine to grow. Do I really want to have 10 or 20 separate components for my projects that all have the same layout? Do I really want hundreds of components for each blog post that has the same structure? It doesn't seem to be very DRY. So the way to do that is to store the data I need somewhere and then just place it over the respective templates. 

Enter PERN. I'm already familiar with PostgreSQL because I use it in my other production apps, and I have familiarity with Node and React. The only one I didn't know much about was Express. I know that I could have simply done a Rails API and I could get it working. But as a developer I'm supposed to be learning new technologies and constantly growing. So I saw this as an opportunity to expand my knowledge base and demonstrate flexibility and adaptability in knowing several ways to create a fullstack application. By my next blog post I hope that I have made some progress, but I am taking the time to read, learn, and practice so that I can do this right. 

Until next time!
