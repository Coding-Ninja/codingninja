---
title: Building A Concurrent Web Scraper With Python
author: zen master
type: post
date: 2013-04-22T08:00:08+00:00
url: /building-a-concurrent-web-scraper-with-python/
dsq_thread_id:
  - 1224699787
categories:
  - Articles
tags:
  - concurrent
  - python
  - web scraper

---
Another week and during my internet travels I stumbled upon a blog post by Aditya Bhargava titled [_“Building a concurrent web scraper with haskell”_][1]. I’m not a Haskell programmer and my experience of it is extremely limited. Reading the post most of it read like a cryptic magic spell!

Anyway it was still an interesting read and has inspired me to try my hand at writing something similar. So I reached out and and the quickest thing to hand was Python. In Linux just fire up a terminal and drop into your favorite text editor and away you go.

**The Process**

It is usually a good idea to think and plan out the basics of the solution design. Our target is a web page and our end result should be all images downloaded from it to disk. The target web page contains links to the images we want to scrape. Once we have a list of images instead of downloading them one at a time, the goal will be to download them “concurrently”.


![A Concurrent Web Scraper Process](http://i.imgur.com/SJBPztV.jpg)


The entire process can be broken down into the following distinct four steps:

  * Get contents of page
  * Parse and create a list of image links
  * For each link start a new thread
  * Download a single image

Now that we have a description of each step (or “function”) we can think about each function’s name and its input and output:

  * “from page” url -> html text
  * “all links” html text -> list of links
  * “in parallel” function, list of links -> start thread
  * “download image” link -> file saved to disk

You may have noticed that the output of one function is the input of another. This has been designed so that each function can be fed into the next one. Thus we can (at least in pseudo code) describe the entire program call:

> in parallel ( download image, all links ( on page ( url ) ) )

Voila we are all done! Erm OK perhaps not quite, we just need to create the code for each function:

Lets create the code in the order that the functions are called. First start off with the parallel call, this function will simply take a “function” to invoke and a list of links. We can iterate through the list, and call the function each time and pass the link to the function as a parameter.



```python
from threading import Thread

def in_parallel(fn, l):
       for i in l:
           Thread(target=fn, args=(i,)).start()
```


<span style="color: #ffffff;">.</span>

To get the html contents for a given url we can use Python’s urllib module:

<pre class="brush: python; title: ; notranslate" title="">import urllib

def from_page(u):
       return urllib.urlopen(u).read()

</pre>

<span style="color: #ffffff;">.</span>

Let&#8217;s now create the function that downloads each image, we need to provide a filename. We could parse out the link that is passed in but being a lazy programmer I&#8217;ve decided to just create a GUID instead :)

<span style="color: #ffffff;">.</span>

<pre class="brush: python; title: ; notranslate" title="">from uuid import uuid4

def download_image(i):
       print "saving -&gt; "+i
       f=open(str(uuid4())+".jpg",'wb')
       f.write(from_page(i))
       f.close()

</pre>

<span style="color: #ffffff;">.</span>

Now all that is left is really the meat of the program, the task of parsing out the image links. To do this I have decided to use regex _(**shudder**; I know I know, you can’t [parse HTML with Regex][2])._ Being naughty sometimes is OK, right?

<span style="color: #ffffff;">.</span>

<pre class="brush: python; title: ; notranslate" title="">import re

def all_links(p):
       links = re.findall(r'href="([^"]+)"',p)
       return [links[i] for i in xrange(0,len(links)) if "http" and "jpg" in links[i]]

</pre>

<span style="color: #ffffff;">.</span>

Finally now that all the functions have been created, we can call it and enjoy the images being downloaded concurrently, and what better web page than reddit’s /r/pics ?

<span style="color: #ffffff;">.</span>

<pre class="brush: python; title: ; notranslate" title="">in_parallel(download_image, all_links(from_page("http://www.reddit.com/r/pics")))

</pre>

<span style="color: #ffffff;">.</span>

**Conclusion**

Programming in Python is fun because the code almost flows in the way you imagine it! Naturally this simple example is most certainly not production ready. However the basics are the same. Extending this example would include limiting the number of concurrent threads, error handling and perhaps recursively calling links on the website. Something for the reader to try out :)

The full 23 lines of source code are included below. Until next time have fun Pythoning!

<span style="color: #ffffff;">.</span>

<pre class="brush: python; title: ; notranslate" title="">from threading import Thread
from uuid import uuid4
import urllib
import re

def in_parallel(fn, l):
       for i in l:
           Thread(target=fn, args=(i,)).start()

def download_image(i):
       print "saving -&gt; "+i
       f=open(str(uuid4())+".jpg",'wb')
       f.write(from_page(i))
       f.close()

def all_links(p):
       links = re.findall(r'href="([^"]+)"',p)
       return [links[i] for i in xrange(0,len(links)) if "http" and "jpg" in links[i]]

def from_page(u):
       return urllib.urlopen(u).read()

in_parallel(download_image, all_links(from_page("http://www.reddit.com/r/pics")))
</pre>

 [1]: http://adit.io/posts/2012-03-10-building_a_concurrent_web_scraper_with_haskell.html
 [2]: http://stackoverflow.com/questions/1732348/regex-match-open-tags-except-xhtml-self-contained-tags