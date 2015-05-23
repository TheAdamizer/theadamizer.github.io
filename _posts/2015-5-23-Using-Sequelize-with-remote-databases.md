---
layout: post
title: Using Sequelize with remote databases
---

For a recent project [inkwell](http://inkwell.adamv.io), I used a node.js ORM that I'm currently
a big fan of: [Sequelize](http://docs.sequelizejs.com/en/latest/).  Sequelize supports a variety of relational
databases, including MySql, SQLite, PostgreSQL and others.  We used MySQL as our database for the project, but we
decided to use a remote database for a couple of reasons.  First of all, it made development on the project more simple in a way because all of our local copies of the server all pointed to the same development database, that way if one of the developers on the project had an issue with a certain entry in a table, we could all immediatly check out that entry as well and start hacking away at the problem.  It's also nice to run a database as a seperate service because then the structure of the backend is more atomitized and manageable.
Luckily, Sequelize makes it very easy to point to a remote database!
In this example, I used a remote MySQL database that I have set up on a super small ubuntu machine (hosted for free through Joyent).  

![Example database configuration](http://i.imgur.com/oC0TE9v.png "Example database configuration")  
As you can see, configuring the database to connect to the server is just as easy as using a local database instance.  There are 4 things that need to be passed into the new object instantiated by the Sequelize class.  
  * The name of the actual database on the MySQL instance. (familyThiefDev in this case)  
  * The user that you will use to access the db.  (root shown as an example)  
  * The password to use for that user. (Obviously and example password)  
  * The connection and database type information in an object.  
   
In this case the object with the type and connection information needs to only contain two key/value pairs.  The first is the actual ip of the host you would like to connect to, and the second is a 'dialect.'  We are using MySQL on my project, but if you wanted to use a different type of a relational database, this is where you would put it.  
This file is a standalone node module, so I just simply export the newly created object and voila!  You have access to a remote database in all of your serverside models, assuming they import your module.  
