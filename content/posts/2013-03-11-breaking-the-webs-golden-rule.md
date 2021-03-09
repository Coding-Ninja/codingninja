---
title: Breaking The Webs Golden Rule
author: zen master
type: post
date: 2013-03-11T09:00:11+00:00
url: /breaking-the-webs-golden-rule/
dsq_thread_id:
  - 1127437323
categories:
  - Articles
tags:
  - best practices
  - golden rule
  - web development

---
The web is an amazing platform, its _“design”_ if you can call it that is ever changing. The web works because it is _“field tested”_ every day by millions of people. That which does not work is simply not used and that which works well spreads like wildfire. The end user devices are diverse and with web platform growth it is no surprise that it has become one massive hack balanced on top of another hack. Web developers over the years have formed unofficial _“Good Practices”_ or _“Golden Rules”_. These rules are not thought up by committees but have been hard lessons learnt from the evolving web.

<span style="color: #ffffff;">.</span>

**Fallbacks and Graceful degradation**

<span style="color: #ffffff;">.</span>
  
For those who may not be familiar with _“Fallback”_ philosophy, one quick definition is as follows:
  
<span style="color: #ffffff;">.</span>

> Fault-tolerance or graceful degradation is the property that enables a system (often computer-based) to continue operating properly in the event of the failure of (or one or more faults within) some of its components. If its operating quality decreases at all, the decrease is proportional to the severity of the failure (Source Wiki)

<span style="color: #ffffff;">.</span>
  
This works very well in regards to HTML as it was always designed to be forward compatible. New elements that are _“bolted”_ on are simply ignored and not rendered. With this process devices that are able to use the new functionality can do so. Older devices can continue to work albeit without the new functions.
  
<span style="color: #ffffff;">.</span>
  
This kind of approach of doing things on the web has thus become a _“Golden Rule”_ and examples of it can be seen in all areas of web development. One such area is that of Javascript fallback.
  
<span style="color: #ffffff;">.</span>
  
Javascript itself was a hack, something added in to make the web a little more shiny. Javascripts humble original use case has now transformed into being a core ingredient of a modern web application or website.
  
<span style="color: #ffffff;">.</span>
  
The huge success of AJAX _(underpinned by Javascript)_ has helped web applications become what they are today. However the need to offer fallback and graceful degradation means that in my view most of these web applications from a design perspective are an architectural mess!
  
<span style="color: #ffffff;">.</span>
  
In order to allow for fallback for AJAX based web applications there are generally two approaches:
  
<span style="color: #ffffff;">.</span>
  
(1) The “HIJAX” approach: Build the site functionality without javascript. Once this is done add in the extra functionality atop of it using javascript.
  
<span style="color: #ffffff;">.</span>
  
(2) Build two separate sites, one with AJAX one without (think GMAIL).
  
<span style="color: #ffffff;">.</span>
  
Both of these approaches are not “clean” design wise. The first one feels like a total hack as the design has split personality. The second approach feels much cleaner as you have two distinct systems. However the downside of having two systems are that it requires twice the effort.<span style="color: #ffffff;"><br /> </span>

<span style="color: #ffffff;">.</span>

**Breaking the rule**

The above solutions are not the only option if you decide to remove the original need for fallback. Once you do away with the need to provide a non-javascript fallback you can avoid the above two options. I’m putting my anti-flame jacket on I can hear the flame throwers firing up :)
  
<span style="color: #ffffff;">.</span>

<div class="wp-caption aligncenter" style="width: 521px">
  <img alt="No fallback? This is madness. Madness? This is AJAAX" src="http://i.imgur.com/c7Gwec8.jpg" width="511" height="307" />
  
  <p class="wp-caption-text">
    No fallback? This is madness. Madness? This is AJAAX
  </p>
</div>

<span style="color: #ffffff;">.</span>
  
Although there are plenty of good arguments for providing fallback for non-javascript users. I’m going to consider the other side for a moment. The first thing I question is how many “non-javascript” users are there?
  
<span style="color: #ffffff;">.</span>
  
Looking at an old stackoverflow answer it appears the best estimate (although old circa 2010) is about 1%. What this suggests is that providing fallback in this scenario is catering for the absolute edge case.
  
<span style="color: #ffffff;">.</span>

> After crunching the numbers, we found a consistent rate of JavaScript-disabled requests hovering around 1% of the actual visitor traffic, with the highest rate being roughly 2 percent in the United States and the lowest being roughly 0.25 percent in Brazil. All of the other countries tested showed numbers very close to 1.3 percent. (source <a title="stackoverflow" href="http://stackoverflow.com/questions/9478737/browser-statistics-on-javascript-disabled" target="_blank">stackoverflow</a> )

<span style="color: #ffffff;">.</span>

<div class="wp-caption aligncenter" style="width: 510px">
  <img alt="Non javascript users" src="http://i.imgur.com/jIE3TFr.jpg" width="500" height="179" />
  
  <p class="wp-caption-text">
    Non javascript users
  </p>
</div>

<span style="color: #ffffff;">.</span>

How important that 1% of users are something that depends on each individual project. For some web sites this number may be too significant to not to consider. I believe that this is not the same case for the majority of projects.
  
<span style="color: #ffffff;">.</span>
  
Another point to be made is if developers continue to provide fallbacks, then the burden to provide javascript support does not exist. In the way as many web developers started to stop making hacks to support Internet Explorer. As a consequence Internet Explorer over the years was forced to become more standard compliant.

<span style="color: #ffffff;">.</span>

**Conclusion**

In 2013 it maybe time to reconsider the need to provide for those who do not have support for javascript. The web has moved on but are the old practices still valid for non javascript support? It may be digital blasphemy to ask, but I feel now the time is right.
  
<span style="color: #ffffff;">.</span>

> “Build it, and they will come”