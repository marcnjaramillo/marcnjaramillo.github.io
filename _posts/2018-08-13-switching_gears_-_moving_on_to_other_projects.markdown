---
layout: post
title:      "Switching Gears - Moving on to Other Projects"
date:       2018-08-13 06:01:43 +0000
permalink:  switching_gears_-_moving_on_to_other_projects
---


For the past month or so, I've been focused on one particular app that I built. Granted, it needed a lot of work to get it presentable; however, I didn't want to neglect other projects that needed attention. This week I did some work on two other projects: my portfolio site, and my final project from Flatiron. First, I want to recap what I have accomplished this past month before I talk about what I did this week.

## Recipe Manager
Over the past month I made major improvements and added some new features:

* Upgrade Rails to Rails 5.2 and take advantage of Active Storage for image uploads
* Use Cocoon for dynamic nested forms
* Implement Devise for smoother login
* New feature - add categories to recipes 
* Improved feature - ensure comments can only be deleted by creator or recipe author
* Update styles - swap out Bootstrap-Sass gem for Bootstrap gem to make use of Bootstrap 4 improvements

## Portfolio Site
I wasn't too happy with where things stood with my portfolio site, and I remember getting pretty frustrated with it. I decided to step away from it for a while, and then I came back to it this week. One of the most frustrating things I was dealing with was how to style it. I built this site soley with React, and I tried to use Semantic UI for styling. I didn't like how it looked, and I didn't particularly want to take the time to learn how to manipulate the CSS to make it do what I wanted it to do because a) I wanted to get my portfolio site up and running ASAP, and b) I was already familiar and comfortable with Bootstrap. One problem though: Bootstrap itself relies on jQuery, which is a library you should avoid using with React. I looked into React-Bootstrap, but it still uses Bootstrap 3 and hasn't been updated to take advantage of what Bootstrap 4 offers. What I ended up using was Reactstrap - an actively maintained package that uses Bootstrap 4. However, I still wasn't really having much success getting it to do what I needed it to do, mostly because my frustration was getting in the way. So, I took a break and focused on another project.

Most of the work I did with my portfolio site centered on understanding how Reactstrap worked and how I needed to make it work with React and React Router. For example, I use Cards to display my projects. Initially the cards contained a brief description of the project and then clicking the "View" button took you to the actual project on Heroku. What I decided to do was create a component for each project that gave a more detailed description of the project and a brief list of skills/technologies used along with a link to the project itself. To make this work I had to figure out how to link the "View" button to that new component. I did this using Route to define the specific routes, and then wrapping the Button in the Link component to make sure it would render the project component. Finally, I wrapped all of the routes in a Switch component so that I would have the component rendered on a new page. 

The last thing that I added to this project was Parralax. I wanted to incorporate something eye-catching to make my portfolio more interesting to look at. I still don't have enough content to really make full use of it, but I am still working on it. As far as future features, I plan to migrate my current blog to this site. I'm also not entirely pleased with having multiple components for projects when they all use the same format. I want to abstract the formatting into a component and then simply inject the content into it, which means I will need to set up a database that my application can communicate with. I would also like to make my life easier by creating forms for new blog posts and new projects, which means that I will need to create an admin backend that only I am able to access. 

## ScheduTerp
I didn't do much with this particular project other than add Bootstrap styles. And that is because I had inadvertently broken it the last time I worked on it. I had forgotten that I had updated my database tables but didn't change any of the logic in the rest of the app. So while it looked like it was working, when I tried to go to parts of the app that relied on the database, nothing worked. The error message I was getting in the console wasn't very helpful, either. It simply said that it couldn't get anything from the database. I thought maybe it was a browser issue, but that wasn't it. Finally, I opened up the app in my local development environment, and the error message indicated that there was a problem communicating with the database because the relation it was looking for didn't exist. When I realized the dumb thing I had done, the fix was easy (albeit time-consuming), and soon I had everything working again.

## Wrap Up
I will still work on the Recipe Manager, but it's mostly polished now. It's time to turn my attention to the other projects I have to get them closer to being production-ready. Until next time!


