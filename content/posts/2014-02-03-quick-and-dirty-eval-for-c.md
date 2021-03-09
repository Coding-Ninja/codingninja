---
title: 'Quick and Dirty Eval for C#'
author: zen master
type: post
date: 2014-02-03T09:00:23+00:00
url: /quick-and-dirty-eval-for-c/
dsq_thread_id:
  - 2204627246
categories:
  - Articles
  - Tutorial
tags:
  - 'C#'
  - Dirty
  - Eval
  - Evil

---
<p dir="ltr">
  <strong>Introduction</strong>
</p>

<p dir="ltr">
  &#8220;Eval is evil&#8221; is a well known phrase and with good reason. Allowing arbitrary code execution opens the doors for [hacker stereotype] to pwn your beautiful application.
</p>

<div class="wp-caption aligncenter" style="width: 510px">
  <img alt="Quick and Dirty Eval for C#" src="http://i.imgur.com/pC03ASA.jpg" width="500" height="300" />

  <p class="wp-caption-text">
    Evil Programmers
  </p>
</div>

<p dir="ltr">
  In many situations the need to reach out to eval is not even needed, its mostly a lazy way out. The price of eval is very high, you pay in terms of speed and security as well as increased debugging complexity.
</p>

> <p dir="ltr">
>   “eval is Evil: The eval function is the most misused feature of JavaScript. Avoid it”
> </p>
>
> <p dir="ltr">
>    Douglas Crockford in JavaScript: The Good Parts
> </p>

<p dir="ltr">
  Of course JavaScript is not the only language to have eval, PHP and many other languages have the ability to evaluate code from strings. The evil uses aside, the ability to evaluate code on the &#8220;fly&#8221; does open up some cool possibilities such as meta programing.
</p>

<p dir="ltr">
  When it comes to C# however the eval function doesn&#8217;t exist (probably a good thing). However I recently needed to visit the dark side, most examples of C# eval are quite verbose, but I managed to put together a fat free version. Its quick and its dirty and you probably shouldn&#8217;t use it but in times of desperation&#8230;
</p>

**Quick and Dirty C# eval in 8 lines:**

```c#
    {
        var csc =   new CSharpCodeProvider(new Dictionary&lt;string, string&gt;() { { "CompilerVersion", "v3.5" } });
        var p   =   new CompilerParameters(new[] { "mscorlib.dll", "System.Core.dll" }, null, true);
        p.GenerateInMemory = true; p.GenerateExecutable = false;
        CompilerResults r = csc.CompileAssemblyFromSource(p, "using System; class p {public static object c(){"+__code+"}}");
        if (r.Errors.Count &gt; 0) { r.Errors.Cast&lt;CompilerError&gt;().ToList().ForEach(error =&gt; Console.WriteLine(error.ErrorText)); return null; }
        System.Reflection.Assembly  a = r.CompiledAssembly;
        MethodInfo                  o = a.CreateInstance("p").GetType().GetMethod("c");
        return                      o.Invoke(o, null);
    }
```
