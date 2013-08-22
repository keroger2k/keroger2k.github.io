---
layout: post
title: "Enums to SelectList"
date: 2012-09-20 16:48
comments: true
categories: ASP.NET, MVC, C#
description: "Turning an Enum into a SelectList"
keywords: "Enum, SelectList, ASP.NET, MVC, HTML Helper" 
---

Recently I had an interview where I was sharing my screen to a couple people who were watching me struggle through the simple task they had me complete.  I had to create a simple drop down list that contain three values and my first thought for whatever reason was to use an Enum and just bind that to a drop down list with the HTML helper object.  However, it had been awhile since I had actually had to do that and after about 1 minute of trying to get it to work I simply gave up and moved on as  I was on the clock.  After the interview I looked back at some code that I currently maintain and found my solution.  It definitely brought back some of the pain that went into the initial implementation.  Although the answer is quite simple, during the pressure of an interview I just couldn’t recall.
Basically, I just used a generic extension method off of type TEnum.  This allows you to just reference a single value of the Enum do a ToSelectList();

{% gist 3726104 EnumExtensions.cs %}

Here is an example usage:

{% gist 3726104 HomeController.cs %}