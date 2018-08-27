---
layout: post
title:      "Hitting A Roadblock"
date:       2018-08-27 07:25:46 +0000
permalink:  hitting_a_roadblock
---


This week hasn't exactly been smooth sailing. I have actually come up against a couple of road blocks that I have yet to surmount. Both roadblocks stem from my attempts to migrate my blog to my portfolio site built on React. I made some progress that can't be discounted, and I have been able to use what I know and implement some new things, but I have to say that it is still frustrtating to not be able to have this one thing completed. 

## Markdown and JSX
The first problem that I have been grappling with and have made some progress with is rendering markdown in a React component. I have tried numerous packages but most of them did not work. I finally was able to get React-Remarkable to work, but it still isn't the cleanest solution. That is because I try to include code snippets in my blog posts whenever I can, and JSX really does not like JavaScript functions or ERB tags because it doesn't know what to do with them. It tries to execute those functions and when it can't, it throws an error. The key is making those functions strings with back ticks and then wrapping the entire thing inside curly braces so that JSX will render the code as it appears. I found this solution from this [blog post](https://medium.com/@jbell714/rendering-code-snippets-in-jsx-react-936746c02bca). That was only part of the battle because I also wanted to style those snippets to look like they do in my Atom editor. I did this using React-Highlight-JS by  placing the code snippets in a Highlight component and identifying the language being used via a className property. Sounds like problem solved, right?

![](https://media.giphy.com/media/l4Ep6uxU6aedrYUik/giphy.gif)

...not so much. You see, to make the Markup component work, it *also* needs to be wrapped in back ticks and curly braces, like so:

```<Markdown>
{`#Markdown example
**Cool stuff!!**
*More markdown*`} 
</Markdown>```

The above works just fine; however, when I try to insert a code snippet:

```<Markdown>
{`#Markdown example
**Cool stuff!!**
<Highlight>
{`function () => (
\\some code stuff here
)`}
</Highlight>
*More markdown*`} 
</Markdown>```

No dice. The braces and ticks within the outer braces and ticks are no longer interpreted as strings. Now that function will be seen as a JavaScript function that needs to be executed, but it will fail. The only way around this? Well...

```<Markdown>
{`#Markdown example
**Cool stuff!!**`}
<Highlight>
{`function () => (
\\some code stuff here
)`}
</Highlight>
{`*More markdown*`} 
</Markdown>```

So when you have to do that repeatedly for several code snippets in a post...

![](https://media.giphy.com/media/yb4Z5l9ttutr2/giphy.gif)

It's not very pretty and it just seems like a whole lot of work. But it works for the time being -- kinda. You see, when I try to display my ERB code snippets, the highlighting is a little off. All of the end tags don't match, and some the opening tags are only partially highlighted. So just when I think I got it figured out, a new problem.

![](https://media.giphy.com/media/g5S8jsJYpGBmo/giphy.gif)

I'm not sure why this isn't working as expected, but I haven't had a chance to really figure out what's going on. It works well enough for now, so until I find a fix, this will have to do.

## So Many Posts - Where To Put Them?
The next issue that I ran into is the fact that storing my posts in a database may not work. For one, I need the posts to retain their HTML tags. Another problem is that my posts all vary in length. This forces me to instead create individual components for each blog post. Not quite the quick and easy solution I was hoping for. Besides that, I have an issue of how to list them all in my blog. I would like to have pagination, but I need to find a more elegant solution than hardcoding. Let me explain. With pagination, I need to provide links for each button so that it renders the correct section when its clicked and the list would update with each blog post that I add. The easiest way to do this would be to iterate over an array and use that to determine what gets rendered on each page. Except I don't have an array. I have separate files with each blog post. I also can't call posts from a database and iterate over that data because it doesn't seem that is a viable solution. The only other thing I could do would require hardcoding and it would just be *WAY* too much work. 

I *could* create Page components and then put blog posts in those pages, and then have pagination at the bottom of each Page that correctly points to "back" and "next" pages, but that would be too much repeated code and it would be very difficult to maintain long-term.

## Final Thoughts
I will continue to research the issues that I've run into and see what I can come up with. I have to stay positve and remember how far I have come. Refactoring and updating my code has been pretty easy up until now. I can't be thrown by a small problem. There will be roadblocks along the way. The important thing is that I understand what I am trying to do and use what I know to help me figure out what I need to learn in order to be sucessful. Until next time!
