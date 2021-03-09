---
title: 7 Productive Tricks That Every Developer Should Know
author: zen master
type: post
date: 2014-07-18T08:00:52+00:00
url: /7-productive-tricks-that-every-developer-should-know/
dsq_thread_id:
  - 2851780164
categories:
  - Uncategorized

---
Software development is really hard and wrestling with complexity is mentally taxing. In business time is money and deadlines add to the stress. Here are some productive tricks that every developer should know to give themselves a boost:

![Productivity Tricks](http://i.imgur.com/6fYzyfI.jpg)

**#1 Testing:**

When doing _any_ testing, _always_ do it in the live production environment! if it works _which it will_ then you save a ton of time and hassle. Don&#8217;t worry about complaints from your end users, use these handy responses:

  * _&#8220;It&#8217;s a user error, you are doing it all wrong&#8221;_ 
  * _&#8220;It works fine on my computer, the problem is clearly your machine&#8221;_ 
  * _&#8220;This is a known bug in your browser&#8221;_ 
  * _&#8220;It&#8217;s an extremely rare race condition, a mute German walrus has a better chance at telling a joke then this happening again&#8221;_ 

**#2 Database Tuning:**

Speed issues? its because you have **too much** data, stop being **greedy** and stop data hoarding. You don&#8217;t _really_ need all this data! and besides you add _new_ records every day! so use this handly one liner 

<pre>DELETE FROM TABLE LIMIT 100000;</pre>

**voila!** speed up is now OVER 9000% , don&#8217;t worry about your boss shaking his clenched fists in the air, that&#8217;s just a **double** fist pump for victory! 

**#3 Passwords:**

Security is hard, the **weakest** point of failure are always passwords. But coming up with and remembering passwords are a pain _right?_

Don&#8217;t worry, everyones knows that the most obvious password is _&#8220;password123&#8243;_. So here is a clever trick, use a **double bluff** by setting your password to _&#8220;password123&#8243;_, because everyones knows no one would
  
be _stupid_ enough to use **THAT** password so you win!

**#4 Source Control:**

Why use SVN or complicated tools like GIT? source control are for **fools!** all you really need is good &#8216;ol email. Its amazing and super secure and in the cloud _(use trick #3 for setting your password to make it _really_ secure)_
  
Need to share your codebase? hit forward and **BAM!**, need to revert to an older version? check your sent folder and **BOOYA!**

**#5 Code Reuse:**

We have all heard about the **DRY** _(Don&#8217;t Repeat Yourself)_ principle, why waste your time retyping the same old same old _huh?_ **copypasta** is your friend, _&#8220;Ctrl+C, Ctrl+V&#8221;_ these are the wizards darkest spell. The more you use it the more code is reused! plus you can fine tune each one independently, Polymorphism baby!

**#6 Backups:**

They say that if you **don&#8217;t** have 3 copies of your data then it does not exist. This is _very_ sage advice indeed so take heed and make sure you store all 3 of them on the **same machine**, because when the time comes and you need your data the
  
_last_ thing anyone wants to do is run around looking for backups _duh!_ Your DevOps people will laugh and cry at you **manically** because of your _genius_ forethought next time the database server blows up.

**#7 Scaling:**

Donald Knuth said it best _&#8220;Premature optimisation is the root of all evil&#8221;_ so don&#8217;t optimise that&#8217;s for **idiots** and **losers** besides life&#8217;s too short to be a human compiler. We all know that hardware gets faster _every_ time you blink, why not let the **hardware** scale for you! not running fast enough? no problemo remember _&#8220;mo&#8217; memory, mo&#8217; scale&#8221;_. Instead of wasting time optimising use this time to play golf with your boss on his Yacht as they say _&#8220;I don&#8217;t optimise, I socialse&#8221;_.

**Conclusion**

So now that you know these amazing super productive tricks, do you have any more of your own? let the world know..