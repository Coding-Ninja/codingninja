---
title: Mountains of Abstraction
author: zen master
type: post
date: 2013-03-18T09:24:53+00:00
url: /mountains-of-abstraction/
dsq_thread_id:
  - 1146241259
categories:
  - Articles
tags:
  - abstraction
  - programming
  - theory

---
As part of my journey to distance myself from Microsoft et al and to the free pastures of open source development. During an uninstall I couldn’t help notice the gigantic size of Visual Studio 2008. I do not recall the exact number, but suffice to say it was possibly a Gigabyte or more; slight feeling of unease came over me.

Does an IDE really need to be this big? To conclude that an IDE is nothing more than a glorified text editor would be both harsh and a slight exaggeration. However the question of size still lingers despite all the modern features.

Software bloat is something I personally dislike. I’ve always gravitated towards lighter options when feasible. Below is a list of software I use often instead of its super sized cousin:

  * Foxit Reader _(~14mb)_ vs Adobe Reader _(installed ~100mb or more)_
  * Google Chrome _(~26mb)_ vs Internet Explorer 9 _(~40mb)_
  * IntelliJ _(~113mb)_ vs Visual Studio 2010 _(~4GB)_
  * Peazip _(~9mb)_ vs WinZip 16.5 _(~56mb)_
  * LibreOffice _(~202mb)_ vs Microsoft Office 2010 _(~3GB?)_
  * MySQL 5.5 _(~31mb)_ vs SQL Server _(requires min 675mb space)_
  * Blender _(~27mb)_ vs 3ds Max _(~4GB)_

The numbers may not be 100% _(ignoring the “apple vs oranges” comparison)_ accurate but they are a sign of the general bloat of “mainstream” software. I can’t answer why some applications are the size they are. My intuition tells me that certainly something is not quite right.

Software development never feels fully satisfying for me nowadays. A big part of me is uneasy not knowing exactly what is going on under all those layers of abstraction.

.What do I mean? well one the one hand, I&#8217;m aware of the basic architecture of a classical computer. I&#8217;m somewhat familiar with adders circuits, and vaguely recall Kirchhoff’s circuit laws. But as we move up the abstraction layers I have knowledge gaps. The problem is knowing that I don’t know!

When chasing the software rabbit down the abstraction hole. Even to produce a trivial GUI screen requires so many things to go on “underneath”. Welcome the mountain of abstraction.

If you are just doing CRUD applications be it desktop based or web based. Not knowing _(or not caring)_ about what goes on underneath may have very little effect on your day to day programming. In that sense the mountains of abstractions are justified, in the quest of keeping the stakeholders happy and meeting those deadlines.

<div class="wp-caption alignnone" style="width: 510px">
  <img title="Mountains of Abstraction" alt="The Problem with Complexity" src="http://i.imgur.com/hdYD8.jpg" width="500" height="294" />
  
  <p class="wp-caption-text">
    The problem of over abstraction
  </p>
</div>

However understanding what goes on under all those layers are still needed. Granted those situations may be limited _(device drivers, graphics, number crunching etc.)_. Another situation would be that of frameworks, these are abstraction layers that on the whole are great for productivity but can have their own disadvantages.

An example of this would be an ORM, while excellent for the majority of trivial CRUD operations. For complex SQL queries a handwritten statement would be far better. ORM’s are a good example of “leaky abstraction” (1).

Issues of leaky abstraction aside, there are other problems. The biggest in my opinion is that of added complexity. The more code that exists for a given feature or function, the more complex it becomes. It is then harder to maintain and the likelihood of failure also increases.

**Summary**

New software frameworks and libraries seem to be pop up every other day. While these are great productivity boosting contraptions. Is the over reliance on these things becoming bad “software culture”?

_“If all I need to do is get to the bakers shop down the road. I’d rather use a bicycle to get the job done, then steam down there in a tank.”_

(1) <http://www.joelonsoftware.com/articles/LeakyAbstractions.html>