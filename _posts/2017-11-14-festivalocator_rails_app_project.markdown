---
layout: post
title:      "Festivalocator (rails app project)"
date:       2017-11-14 22:56:05 +0000
permalink:  festivalocator_rails_app_project
---


![](https://cdn-images-1.medium.com/max/1600/1*wssl9pVpfu868Tu6nPBCAQ.gif)

Everyone likes travelling and attending festivals all around the world, however, after a little bit of research I found out that there isn’t a website that would collect all the data about music and film festivals around the world, allowing people easily to see the list of upcoming festivals in a certain part of the world, without having to use events websites that have a ton of other events and features unrelated to the topic.

I have decided to try and build an app, which would aggregate first only film and music festivals, but probably in future expand and include other types of art festivals.

Festivalocator app is built using Ruby on Rails framework. In order to implement an easily manageable system of users creation and authentication I used a gem called Devise, and also later added for authorization the Pundit gem in order to separate admins from regular users. Mostly admin’s role is to check all the festivals recently added by users, verify, and approve them, so that they show up in the search. In order to make the registration process easier I have implemented Google and Facebook login functionality with the respective omniauth gems.

After logging in the user is invited to explore all the available festivals, which can be filtered by Location (part of the world) and category.

![](https://cdn-images-1.medium.com/max/1600/1*sumEGG-Kn0i8DvxHvEA7Vw.png)

After selecting a festival, the user is taken to the details page, which lets the user save the festival or mark that they are attending it. Also other attendees and interested users are displayed on the page.

![](https://cdn-images-1.medium.com/max/1600/1*FyGwYaGchZodMnLRydtPvQ.png)

Any registered user can submit a new festival, but it has to be approved by an admin for it to show up on the explore page.

![](https://cdn-images-1.medium.com/max/1600/1*b2_E_gt45_uO0WPOu3WMDQ.png)

One of the problems that I encountered is finding an API for music and film festivals or a source from which I could scrape the data. A lot of events APIs are available, like Songkick and Eventful, however they do not separate festivals from the regular events. The solution and alternative for manually adding the data is yet to be figured out.

In addition to figuring out an automated way to expand the database of festivals, I would also like to work on new functionality such as publishing the festival that a user is attending on their facebook page.

Please check my app by visiting [festivalocator.herokuapp.com](http://)!




