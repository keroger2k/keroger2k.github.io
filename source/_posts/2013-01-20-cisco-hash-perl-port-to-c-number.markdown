---
layout: post
title: "Cisco::Hash Perl Port to C#"
date: 2013-01-20 16:46
comments: true
categories: C#
description: "Converting Perl Cisco::Hash into C# code"
keywords: "Perl, C#, Cisco, Hash, Password" 
---

Recently had to write a script that looks at passwords on cisco devices.  This small piece of code is a port of Perl’s Cisco::Hash module to C#.  Nothing fancy but it works.  Don’t have a need for the encrypt portion so I didn’t add that just yet.  Maybe later.

{% gist 4457022 IOS7Crypt.cs %}