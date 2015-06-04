---
layout: post
title: Test your Express-JWT back-end with postman
---

[Postman](https://chrome.google.com/webstore/detail/postman-rest-client/fdmmgilgnpjigdojojpjoooidkmcomcm?hl=en), if you're not aware, is an awesome REST client that works through chrome as an app.  Among many other things, it
allows you to try out your back-end on your new project as you work on it!  Of course, this is no substitute for good unit testing, but sometimes we just need to check out if a feature is working as planned quickly rather than write
out a whole spec for the new feature.  However, maybe your new route is authenticated with Express-JWT and you're having trouble figuring out how to get postman to access it?  I've got your back.  
  
First of all, grab postman if you haven't already, start it up, and start running your back-end you'd like to test.  First, let's login using postman by POSTing to your login route.  
![Send the login post](http://i.imgur.com/i8ZRgO8.png "Login with Postman")  
Next, you'll get a token key as your response body.  
![Copy the token](http://i.imgur.com/p8dkBwb.png "Copy the whole token from the response")  
Copy that for use in your authenticated requests.  For the last step, simply create a new request on any authenticated route and edit the headers for it so that they contain the token on the shown key.  
![Paste the token into the new header](http://i.imgur.com/En8gzP0.png "Paste the token into the new header")  
Voila! You should be able to make requests to any of your authenticated routes now! Isn't postman awesome?  