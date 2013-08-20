---
title: "Up and running with Sinatra"
date: 2012-06-01 00:13
comments: true
sharing: true
categories: [Sinatra, Ruby, Mustache]
---

## Introduction

I've been playing around with ruby on rails for quite some time now.  Although I'm primarily a
.NET developer, I find rails a very interesting framework to develop with mainly because of the 
community that is built around rails.  From inception to initial deployment can be minutes with
scaffolding, gemfiles and heroku at your disposal.  The community for rails is tremendous and just
about everything you can imagine has already been thought of and a gem created for you.  In the .NET world
only recently have we had something similar with [NuGet](http://nuget.org/) and that has made quite an impact on how
things are done within the .NET world.  

To get a better understanding of how rails works, I've been trying out the microframework called [Sinatra](http://www.sinatrarb.com/).  Sinatra is a very lightweight framework that doesn't abstract away a lot of what is truly happening.  


## Getting Started 

To get started create a simple directory framework for an application that for now will just serve up static content:


```
- Hotel
	- App\
		- app.rb
		- boot.rb
		- hotel.rb
	- Gemfile
	- Rakefile
	- config.ru
	- Procfile
	- Readme.md
```

The 'Readme.md' file is mainly for use with [github](http://www.github.org).  Github uses the readme file
for a way for the  author to explain the purpose of the application along with any helpful syntaxes, scenarios etc...

The Gemfile is what tells ruby what the dependencies are required to run the application.  You want to make sure you have
the Gemfile located in the root directory and the very first line should be a link to the source for the gems.  In this
example rubygems.org is being used.  Below the source are the list of gems that are required to get the sinatra
application up and running.  

- rack (middleware that sits between your application and the server.  Handles API calls, HTTP params, etc...)
- rake (software specifically designed for task within your application)
- sinatra (Lightweight, simple, powerful DSL (Domain Specific Language) developed for ruby and reliant on rack)
- mustache (templating framework for views)
- foreman (Process management for Procfile-based applicaitons.)
- thin (Webserver used to run application.)

A lot of the gems above I used because [Heroku](http://www.heroku.com).  It just makes things easier for me.  There are a lot of great alternatives to mustache, thin, etc..., but I'll be using these in my examples.  There are also some gems for testing that I like to use, but they are not required for getting up and running.

{% gist 2848476 Gemfile %}

The procfile is what foreman uses to start the thin webserver.  In the example below it is telling the thin webserver
to start up and use port 5050.  Once the webserver is up and running you will be able to preview the results by going to
<http://localhost:5050>.

{% gist 2848476 Procfile %}

The config.ru file is executed when the application is starting and instructs the application
to require certain libraries that we've included.  In this example I've put most of the require statements in a file called boot.rb and the first line is giving it the location to that file for the includes.

{% gist 2848476 config.ru %}

The boot.rb file isn't required, because it could all be put into the config.ru file, but this is a nice way
to keep the require statements for the application in a centralized place.

{% gist 2848476 boot.rb %}

Using rake can be extremely powerful.  It allows you to configure common tasks within your application.  In the startup example there is only one task that needs to be performed, starting the application itself.  In this example it is telling foreman to start which in turn will read the Procfile in the root directory and foreman will start the thin webserver on the port 5050. 

{% gist 2848476 Rakefile %}

The app.rb is the meat of the application so far.  This class inherits from Sinatra::Base.  This is the base class for all Sinatra applications.  Here we are telling our Sinatra application to respond to only the "/" GET request.  So any other request currently will return a 404.  If a "/" GET request is received it will simply respond with the current time on the server.  Nothing fancy but proves that Sinatra is up and running correctly.  You will need to understand the different HTML
method definitions to layout responses for your Sinatra application.  The most commonly used methods are GET, POST, PUT, DELETE.

{% gist 2848476 app.rb %}

Here is where application specific logic will be stored.  Nothing is currently required so this is an empty class currently.

{% gist 2848476 hotel.rb %}


Once all theses file are created and in place.  Run 'rake start' and visit <http://localhost:5050> to see the current time on the server.  


## Conclusion

In this first post of mine I'm not really showing too much of the functionality of Sinatra itself.  It is basically a guide on how to get up and running and what is required.  Although there is much less required to get started I think this is a good structure to start with for real applications.  If you want a bare bones up and running introduction the [Sinatra](http://www.sinatrarb.com/) has some great examples.  
