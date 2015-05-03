---
layout: post
title: Automatic depolyment with Github Auto Deploy 
---

Recently I found a pretty nifty tool while trying to homebrew a continuous integration system based on
github's webhook system.  While there are plenty of awesome systems out there, I kinda wanted a system that
I had full control over and I wanted it to be local to my deployment server so that I don't rely on a system
I have nothing to do with.  This tool, Github-Auto-Deploy, is a simple web server running on python that listens
to post requests from github's api and acts accordingly.  A simple config allows you to specify the github repo 
url that you would like to listen to requests for, then it navigates to a specified folder on your server (which 
should be a initilized git repo) then runs a git fetch in that repository.  Afterwards it runs a custom script.
In order to make this work as a constant deployment system, I wrote a simple script that does a git pull after the
fetch to update the repo.  It would be simple enough to chain a grunt/gulp task afterwards to initialize an 
automated build/test/deploy process, that way you always have server that's up to date with your master branch!
