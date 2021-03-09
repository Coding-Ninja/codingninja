---
title: Coding Ninja Reloaded
author: zen master
type: post
date: 2021-03-09T02:00:00+00:00
url: /coding-ninja-reloaded/
categories:
  - Article
tags:
  - blog
  - DevOps
  - hosting
---

I had totally forgotten that I started a blog way back in 2012! seems time has flown by! In that time I've made a few changes to how the site was hosted: at first it was hosted from my bedroom "server" _(fun times)_, then eventually in the "Cloud" and then it was dumped onto Google Firebase.

![Build All the things](https://i.imgflip.com/50z7vf.jpg)

The original version was my own custom built CMS written in C# because as a young-ish and naive developer with "Not Invented Here" syndrome _"build all the things"_ was clearly the way to do development. Later on as I ran out of motivation to add newer features I eventually did the sensible thing and switched over to WordPress which was "ok" I guess. Eventually when I had more sense I migrated the whole thing over to a static site using a static site generator. And yes at one point I was tempted to build a site generator, but thankfully the real world and time brought me back to my senses. 

The theme has also changed a few times. While there was nothing really wrong with the last theme, I decided for a new fresh "break" and so have picked and tweaked a new theme for this blog as part of the "reload". In that process I've also decided to _"prune"_ and nuke some older posts. If for some reason you needed those deleted posts I am truely sorry its gone! _(but you could always use way back machine)_

Finally I've moved off Google Firebase and over to the new _"hotness"_ or _"kind of new hotness"_ by running off on CloudFlare's pages. I like CloudFlare pages because I can just use GitHub instead of some custom Google tooling to handle the deployment.

```shell
$ git add .
$ git commit -am 'until next time, keep on building'
$ git push origin main
```
