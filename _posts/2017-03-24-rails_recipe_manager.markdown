---
layout: post
title:  "Rails Recipe Manager"
date:   2017-03-24 17:30:06 +0000
---


It's been a while since I last posted something. The last four months have been challenging for a lot of different reasons, so I had to take a step back from the blog. I also had a hard time focusing on writing code for extended periods of time, so I had to proceed slowly. But I *finally* completed my Rails portfolio project! Most of my time these last few months has been spent reading documentation on associations, watching videos, playing with the console...just trying to make sure I understood what I was doing. 

For example, the project required that I make use of class-level scope method. I wasn't exactly sure how I was going to implement this, mostly because I couldn't really remember what a scope method was. Rather than spending time searching through previous lessons I looked through the Rails API documentation and other resources. What I found is that it is essentially a regular class method, but written a little differently. So this:
```
scope :search, lambda {|search| where(["name LIKE ?", "%#{search}%"])}
```
is essentially the same as this:
```
def search(search)
     where(["name LIKE ?", "%#{search}%"])
end
```
Another thing that I had to spend some time practicing is method chaining. This was particularly frustrating when trying to get my recipe form to work right. Even after finally getting that right, I wanted to pull my hair out when trying to figure out why the recipe I created wasn't being associated to my user! As I did some more digging I found that my form wasn't associating the foreign key of `user_id` to the recipe. After adding one single line to the code, I got it to work!

It has been a long and frustrating journey to get here, but I'm glad I finally made it. I'm really happy with the app I created, and that's really what matters.
