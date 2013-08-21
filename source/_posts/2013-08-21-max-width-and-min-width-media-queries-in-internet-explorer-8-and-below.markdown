---
layout: post
title: "max-width and min-width media queries in internet explorer 8 and below"
date: 2013-08-21 15:12
comments: true
categories: 
---

Ever since [Twitter Bootstrap](www.twitter.com) came about I've been a huge fan.  It has been an awesome framework to utilize when working on rapid development and prototyping solutions for customer requirements.  For people who are not really UI strong, bootstrap has been a savior.  

Recently I was working on website that I wanted to ensure was compatible with Internet Explorer 8 and I was using bootstrap.  After working on the page for a day or so in [Chrome](www.google.com/chrome) I thought it would be pretty close to identical.  I was wrong.  Bootstrap uses a CSS class called <code>.container</code> to mark the body of the document.  It has a <code>@media</code> query that sets the size of the <code>.container</code> class based on the size of the screen.  This allows for responsive design on desktops, tablets, phones, etc...  After a bit of searching on the web I discovered that although IE8 does respond to some <code>@media</code> queries it doesn't recognize <code>max-width</code> or <code>min-width</code>.

[Resond.js](https://github.com/scottjehl/Respond) to the rescue.  

{% blockquote %}
How's it work?

Basically, the script loops through the CSS referenced in the page and runs a regular expression or two on their contents to find media queries and their associated blocks of CSS. In Internet Explorer, the content of the stylesheet is impossible to retrieve in its pre-parsed state (which in IE 8-, means its media queries are removed from the text), so Respond.js re-requests the CSS files using Ajax and parses the text response from there. Be sure to configure your CSS files' caching properly so that this re-request doesn't actually go to the server, hitting your browser cache instead.

From there, each media query block is appended to the head in order via style elements, and those style elements are enabled and disabled (read: appended and removed from the DOM) depending on how their min/max width compares with the browser width. The media attribute on the style elements will match that of the query in the CSS, so it could be "screen", "projector", or whatever you want. Any relative paths contained in the CSS will be prefixed by their stylesheet's href, so image paths will direct to their proper destination
{% endblockquote %}

After adding the <code>respond.js</code> script tag in my <code><head></code> tag and refreshing the page my problem was solved.  I also used a conditional clause to only load the script for IE8 or less.

{% gist 6299948 %}

Hope this helps someone.  Not that it was a hard problem to solve, but it was shocking that Twitter Bootstrap didn't account for this issue.  Good luck.