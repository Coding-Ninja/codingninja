---
title: Magic Numbers and Being Naughty
author: zen master
type: post
date: 2013-03-04T09:00:13+00:00
url: /magic-numbers-and-being-naughty/
dsq_thread_id:
  - 1116170919
categories:
  - Articles
tags:
  - magic numbers
  - query
  - sql
  - tuning

---
Another week in development at a finance company, the cyclic experience of which many developers will probably recognise. An endless list of requirements along with project hopping and finally a side sprinkle of meetings to top it all off.

Sometimes in this manic loop the condition is broken with something that makes you smile a little. Last week a funny little thing happened and I wanted to share.

&nbsp;

**Curious metrics**

My colleague breaks my laser focus away from reddit, sorry I meant my work on &#8220;business critical&#8221; features _“Calculate_Tax()&#8221;_ and _&#8220;SolveTravellingSalesManProblem()”_. Of course these features were supposed to be ready yesterday but I guess them being late a few more hours at this point would not make any difference.

“I’ve been running SQL profiler, just spotted this stored proc, seems to be consistently slow” he says pointing at the screen.

“Really? What? that proc is fairly trivial, it shouldn&#8217;t take that long. Lets have a look at the execution plan” I respond as I pull my chair up closer.

We spend the next few minutes looking at the stored procedure, looking for _anything_ obvious. Switching over to the test environment, we make some quick changes.

“Lets run it again, see what difference it makes this time” I ask with bated breath. Hit F5 and we patiently watch the loading animation whirl around and around.

“Same as before! that has made no difference at all” my colleague says with disappointment. Ok so lets now read it line by line.

The following SQL code has been modified to serve as an illustration of the problem:

&nbsp;

<pre class="brush: sql; title: ; notranslate" title="">declare @foo int
declare @bar int
declare @baz int

set @foo = some_Id_1
set @bar = some_Id_2
set @baz = some_Id_3

select
           [multiple columns]
from
           [multiple tables joined]
where
           (some_col = @foo and some_other_col = @bar)
            and
           (bla bla...)
</pre>

&nbsp;

First we removed unnecessary joins, that didn&#8217;t make any difference. Next we changed some of the joins to “inner joins” were possible, still no difference. We started changing the logic out, doing separate queries then merging the data. The number of joined tables was reduced but still no cigar. A ping pong of running, looking at the execution plan, tweaking and running again. Things are not making any sense, the stored procedure did not have any of the typical signs of things that would cause it to execute slowly. 

&nbsp;

<div class="wp-caption aligncenter" style="width: 310px">
  <img alt="SQL! my brain is full of f*ck" src="http://i.imgur.com/WsGbvyF.png" width="300" />
  
  <p class="wp-caption-text">
    SQL! my brain is full of f*ck
  </p>
</div>

&nbsp;

**Magic numbers**

Only one thing seemed to remain. The **“where”** clause used variables that were declared and then set to an integer. Of course using nice variable names is “good practice”. Most developers have probably heard of the evils of **“Magic numbers”**[1].

Following this practice in order to make the stored procedure read more easily, nicely named variables were used. This helped when it came to reading the query as well as for maintenance. 

Just to humour our curiosity, we decided to copy and replace all the nice variables with hard coded constant magic numbers. We hit F5 and and to our surprise the query returned in milliseconds.

Good news, but why should hard-coding make such a difference? At this moment I must admit I&#8217;m not an expert in the inner workings of the query optimizer and execution engine. Only as a speculation I suspect that perhaps when the optimizer encounters a variable it must cater for a range of possible values. When the optimizer encounters a hard coded constant perhaps it can optimize further than before because of the constrained values.

If anyone reading this knows exactly why hard coded magic numbers work so well please do comment and let me know.

> The term magic number or magic constant also refers to the programming practice of using numbers directly in source code. This has been referred to as breaking one of the oldest rules of programming, dating back to the COBOL, FORTRAN and PL/1 manuals of the 1960s.[6] The use of unnamed magic numbers in code obscures the developers&#8217; intent in choosing that number, increases opportunities for subtle errors (source wikipedia) 

&nbsp;

**Conclusion**

Best practices are there for a very good reason. In the constant battle between business demands and development sanity “best practices” are on our side. So when we don’t conform to best practices it can feel a bit naughty, putting magic numbers in your code is therefore naughty. Sometimes, just sometimes its good to be a little naughty.