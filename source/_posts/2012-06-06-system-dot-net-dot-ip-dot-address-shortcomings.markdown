---
layout: post
title: "System.Net.IP.Address Shortcomings"
date: 2012-06-06 15:35
comments: true
categories: ASP.NET, MVC
description: "Dealing with the lack of support for a true IPAddress object within .NET"
keywords: "asp.net, C#, ipaddress, system.net.ipaddress" 
---

#Overview

Perhaps I'm going about this completely the wrong way, but from what I can tell, there really isn't much logic built into the framework for IP Addressing and C#. There is a [System.Net.IPAddress](http://msdn.microsoft.com/en-us/library/system.net.ipaddress.aspx) class that has some very limited capabilities IMO. I just don't understand why there isn't some additional functionality with this class or some sister class that helps simplify common tasks with IP address functionality. For example an IP address is mostly useless alone. Without a subnet mask you have no real sense of the IP address. Once you have the subnet mask you then can extrapolate all the details such as network address, broadcast address, size, etc... I wish the System.Net.IPAddress class allowed you to do more things like this natively.

Below are a few methods to help extend on the logic of System.Net.IPAddress. I thought I'd share what has been completed so far. I've also included the NUnit test cases that go along with this class to help with understanding what each of the methods are doing.

#The Code

{% gist 2884281 IPHelper.cs %}

#The Tests

Here are a few test to ensure the validity of the IPHelper class. I know there are probably a lot more test I could create, but right now this has covered everything. So far so good.

{% gist 2884281 IPHelperTests.cs %}