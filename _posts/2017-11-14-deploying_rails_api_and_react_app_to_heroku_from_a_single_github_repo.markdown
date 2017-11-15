---
layout: post
title:      "Deploying Rails API and React App to Heroku from a single GitHub repo"
date:       2017-11-14 19:51:15 -0500
permalink:  deploying_rails_api_and_react_app_to_heroku_from_a_single_github_repo
---

If you are looking to deploy your final project to Heroku and you took the same unwise path like me and created a single repo on GitHub for your final Learn project, instead of two separate ones for Rails API Backend and React Client-side apps, this blog post might be helpful. 

Unfortunately Heroku can not automatically identify your two different apps contained within a single repo, but as always there is a nice workaround to solve this problem. 

Start with creating two separate apps on Heroku, let's call them 'your-heroku-rails-api-app' and 'your-heroku-react-app'. 

Deploy your Rails API with the following steps in your Terminal console:

1. cd into Rails App folder from the root folder that is pushed to your repo
2. `heroku git remote -a your-heroku-rails-api-app`
3. `git push heroku master`
4. cd back into your root folder
5. `git subtree push --prefix rails-api-project-folder-name heroku master`

Important steps to take after: 
1. Don't forget to migrate your database to Heroku with `heroku run rake db:migrate`. Run this command while in Rails API project folder.
2. If you have any environment variables set in your .env file that is added to git ignore file, set them up on Heroku by going to your applicatoin Dashboard -> Settings -> Config Variables.

Deploy your React App with the following steps in your Terminal console

1. cd into React App folder
2. use buildpack that deploys a React UI as a static website: `heroku create -b https://github.com/mars/create-react-app-buildpack.git`
3. `heroku git remote -a your-heroku-react-app`
4. cd back into your root folder
5.  `git subtree push --prefix react-app-project-folder-name heroku master`

Important steps to take after:
1. In your React Project root folder create a new file called static.json with the following content:
```{
  "root": "build/",
  "routes": {
    "/**": "index.html"
  }
}```


This will prevent you from getting an annoying 404 error everytime you navigate directly to any route that is not '/' in your app.

Now that you can share your project with your friends and Learn community, dance!
![](https://media0.giphy.com/media/8j3CTd8YJtAv6/200w.webp#32-grid1)



