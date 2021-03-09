---
title: Go Home Bob You're Drunk
author: zen master
type: post
date: 2017-12-05T00:15:00+00:00
url: /go-home-bob-you-are-drunk/
categories:
  - News
tags:
  - response
  - sql
  - programming

---

_what follows is a tongue in cheek response, hopefully Bob is cool:_

Ah good 'ol Uncle Bob (_Robert C Martin_), made a blog post a few days ago entitled ["Bobby Tables"](http://blog.cleancoder.com/uncle-bob/2017/12/03/BobbyTables.html) (_most likely a reference to this [xkcd](https://xkcd.com/327/) post_):


![xkcd](https://imgs.xkcd.com/comics/exploits_of_a_mom.png)

Great **xkcd** post as always it's funny because its true: [sql injections](https://en.wikipedia.org/wiki/SQL_injection) are bad, like really _bad_.

I'm not sure if Bob was actually drunk, but the logic that follows is erm, not right: Since SQL injections are possible, ergo _SQL_ is flawed?

Bob then makes a radical announcement:

> here's an idea **STOP USING SQL!**

Woah hey Uncle Bob, slow down there! lets not just throw the baby out with bathwater shall we?

SQL is just fine, unsanitised user input on the other hand is akin to self harm. Like the good Dr tells us "if it hurts stop doing it". Are there **idiots** still out there making these mistakes? most likely, but sadly we can't just fix stupid. Is sanitising inputs and using proper parameterised sql hard or _arcane_? not really, in fact there is no excuse, almost every modern framework or library can do this (_if not, lol no sql sanitising_)

Bob goes onto drive the message home, voice now _slurred_ and dazed:

>  so long as there is a SQL engine in the system, there is simply no reliable way to guarantee that such an attack can be prevented?

If only there was some kind of automated tool, a tool that could test for sql injections oh my! (3 google seconds later):

```shell
sql injection penetration testing tools
```

Holy batman, look!! 509K hits, such results, much hits! so happy


**Conclusion:**

Keep calm and carry on using SQL (_sanitised sql of course, we're not savages after all_) 
