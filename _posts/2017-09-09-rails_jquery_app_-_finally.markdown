---
layout: post
title:  "Rails/jQuery App - Finally!"
date:   2017-09-09 22:28:55 +0000
---


I started working on this project a couple of months ago, and I'm *finally* done! It took me a lot longer than I anticipated, and life had plenty of roadblocks for me to deal with along the way. I'll try to talk about a few of the things I had to deal with in updating my app for this project.

## Rendering 'show' and 'index' pages without page refresh

The first thing to take care of was using jQuery and Active Model Serialization (AMS) to render an index page and a show page without a page refresh. I chose to use the `/recipes` index and show pages for this requirement. To get started, I installed the `active_model_serializations` gem. I then created serializers for my recipes, ingredients, and users. I then updated my controllers to render json for the correct controller actions. Once that was done, I watched this [video](http://instruction.learn.co/video_lectures/146) to figure out how to render the pages without a refresh. After I was done, I had these two objectives completed.

## Create a resource using jQuery

This is the one that gave me the most trouble. I tried creating additional ingredient resources, but I kept running into roadblocks. Instead, I decided to just create a new feature - comments. Once I generated the resource and wrote the controller actions, I set up the serialization and created the form for comments. The last step was writing the Javascript for adding comments without a page refresh.

## I couldn't have done it alone

I have to acknowledge the help that I got from my instructor for this project. He was very helpful in walking me through some of the obstacles I had and working with me during some office hour sessions. He suggested the video for me to watch and even took a look at my code a few times to give me some suggestions. I definitely appreciate the help that all of my instructors have given me during my time in the program.
