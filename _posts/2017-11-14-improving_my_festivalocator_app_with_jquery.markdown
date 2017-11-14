---
layout: post
title:      "Improving my Festivalocator App with jQuery"
date:       2017-11-14 22:59:44 +0000
permalink:  improving_my_festivalocator_app_with_jquery
---


My previous story was about Festivalocator, a Rails application for exploring music and film festivals from all around the world. Following my Learn.co assignment I’ve made some improvements on the front end side of the application.

**1. Filtering festivals and updating results on the page with AJAX**

Previously the page would reload every time after the user selected some filter parameters and hit “Filter” button. In order to avoid that, I added a filterFestival() function. This function grabs values of filter input fields, sends an AJAX request with the right search parameters, then renders the response inside the same container with festivals. The challenging part here for me was figuring out how to grab filter values from a drop down input. Adding “option:selected” to the selector solved the problem.

```
$(‘[name=”category”] option:selected’).text()
```

**2. Displaying festival comments and adding new ones using AJAX**

After adding a new has_many comments association to festival model, I decided that it would be cool if the comments section would appear on the festival page on click of “show comments” button, so I added an event listener and created a showComments() function that sends two AJAX requests to render the “index” of comments and the “new” comment form to the page. Attaching another event listener and preventing the default action of the “Create Comment” button allowed me to add new comment content to the page without the page reload.

**3. Rendering edit form on the show page, submitting it and displaying updated festival using AJAX**

I have updated the show page to render the edit form in place of the festival information when the “Edit” button is clicked. The form is then submitted using AJAX, and the response of the PATCH request returns in the form of JSON. To make that happen I used gem ‘active_model_serializers’, that allowed me to have access to the festival show page in both HTML and JSON formats. Active Model Serializer enabled me to create some custom human readable properties for category, world part, and date. Category and world part would otherwise have been represented in the form of ids. For the convenience of rendering the show page using JSON data, I have created a Javascript Object Model and utilised the Handlebars template processor inside the show festival view.
