---
title: The Cult Of Unit Testing
author: zen master
type: post
date: 2013-04-15T08:00:59+00:00
url: /the-cult-of-unit-testing/
dsq_thread_id:
  - 1208751977
categories:
  - Uncategorized
tags:
  - Complexity
  - Cult
  - Testing
  - Unit

---
<p dir="ltr">
  There are many things that sound great in principle, and sometimes a few of those things can even work out in practice. These rare gems should be shared with others right? People like to spread the good word. In time though the idea gets jumbled with other things. In its new corrupted form things stop working <em>“in practice”</em>. However the old stories live on, an affirmation that it is still a great idea. A <strong>cult</strong> is born and in the presence of this cult even the thought of questioning it will unleash wrath from the gates of conformity.
</p>

<p dir="ltr">
  Programming in one sense is the art of controlling complexity, the human brain are limited. It is very easy to take a simple task and add more complexity to it. If we are not careful we can get killed by the blast of complexity explosion. Once the complexity exceeds our capacity to comprehend it, that is when system instability are inevitable.
</p>

Debugging a problem is an attempt to understanding state behavior  Fixing a bug are catering for a system state or edge case that was not envisioned before.  It is thus not surprising the less you know about a system, the less you can predict its various states and behaviors.

<div class="wp-caption aligncenter" style="width: 510px">
  <img alt="Unit testing like riding with the training wheels on" src="http://i.imgur.com/3mpl2Bx.jpg" width="500" height="333" />
  
  <p class="wp-caption-text">
    Unit testing like riding with the training wheels on
  </p>
</div>

<p dir="ltr">
  <span style="color: #ffffff;">.</span>
</p>

<p dir="ltr">
  In an effort to stop the rise of system instability, unit testing has been seen as a way to fight it. An elegant solution in <strong>principle</strong>: write code that verifies the behavior of a <em>“unit”</em> of code. Once a set of <em>“unit tests”</em> are written the process of code verification is thus automated. Code changes can be made with total confidence. Its like riding a bike with the training wheels on, you are <em>never</em> going to fall over.
</p>

<p dir="ltr">
  There are a long list of arguments against unit testing, with those arguments there are counter arguments. However none of those arguments deal with the deep rooted failure of the principle itself.
</p>

<p dir="ltr">
  What is that failure? The failure is the base assumption that the unit test can encompass <em>ahead</em> of time the full set of system states and edge cases. This is <strong>contradictory</strong> because the reason bugs occur are because we are not able to envision ahead of time all cases. How can we then begin to write tests for things we don’t even know exist?
</p>

<p dir="ltr">
  Does this mean unit tests are useless? <strong>No</strong> unit tests can be used in very special cases I believe. An example of a special case would be an algorithm, in this case it makes sense because you can know what to expect and thus test against it.<b><b> </b></b>
</p>

<p dir="ltr">
  OK if unit tests can not fight the rise of system instability what then are the alternative solutions?
</p>

<p dir="ltr">
  In my humble view I would suggest that we go back to the root, the failure to predict state and behavior  This will never be solved<em> (bugs will thus always occur)</em> however the more we can understand a system the rarer those cases become.
</p>

<p dir="ltr">
  Instead of endless unit tests, start by <strong>reducing</strong> system complexity, refactor mercilessly even rebuild from the ground up when needed. This is not a perfect solution <em>(there are no silver bullets)</em> think more of “water resistant” than “water-proof”.
</p>

<p dir="ltr">
  <strong>Conclusion</strong>
</p>

Unit tests are pushed in an almost cultist way. Among the cult those that do not use unit tests are seen as knuckle dragging neanderthals or unenlightened. If you want increased stability you will need to first control complexity, to do that you need to reduce it. Unit test are thus band aids trying to **work with** complexity _instead_ of reducing it.

> Beauty is more important in computing than anywhere else in technology because software is so complicated. Beauty is the ultimate defense against complexity. (David Gelernter)