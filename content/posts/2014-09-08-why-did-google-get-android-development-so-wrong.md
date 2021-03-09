---
title: Why Did Google Get Android Development So Wrong?
author: zen master
type: post
date: 2014-09-08T08:00:14+00:00
url: /why-did-google-get-android-development-so-wrong/
dsq_thread_id:
  - 2998115089
categories:
  - Articles
  - Reviews
tags:
  - android
  - Development
  - google
  - Kivy
  - python

---
**Introduction**

It is 2014 and the mobile is the _new_ frontier, we are probably past the transition point of going from mainstream web to mainstream mobile in terms of usage and its a hopelessly **messy** affair for developers. If web development appeared untamed and wild and ugly back in the 90’s then mobile development is now a whole new level of **ugliness**.

Like the albatross that was Internet Explorer, Android today are the developer’s _new_ albatross. Google has used its muscle to push its way to the top spot and now can claim to be King of the Hill. If you want to develop for the mobile market, it would be commercial _suicide_ to ignore the Android market.

![broken](http://www.codingninja.co.uk/wp-content/uploads/2014/09/broken_android.jpg)

Android development to put it _mildly_ is a pain in the rear side. Programmers do not usually develop for Android because they **want** too, like Internet Explorer it is because they _HAVE_ too.

There are numerous blog’s already on the internet written by many a burned developers that have had to endure the **punishment** that is Android development. I don’t _need_ to add to that hall of **anguish**.

Everything from installation, environment setup, **stupid** and over engineered SDK, device fragmentation, lack of consistent and current documentation has already been covered by many before me. I don’t want to cover those points in this blog post, instead I want to talk about a _different_ way. What if I told you that Android development didn’t have to suck? what if I told you there was another way?

**Another way, the Python way**

What if you could just issue a few simple commands and have an entire environment set up for you? 

```shell
sudo add-apt-repository ppa:kivy-team/kivy
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install python-kivy
```

What if instead of installing a mammoth IDE and configuring it you could just open a text editor and simply program it _(in a beautiful language)_?

```python
import kivy
from kivy.uix.widget import Widget
from kivy.app import App


class HomeScreen(Widget):


	def button_clicked(self):
		self.ids.home.counter += 1
		self.ids.label1.text = "you clicked " + str(self.ids.home.counter) + " times!"


class MyApp(App):

	
	def build(self):
		return HomeScreen()


if __name__ == '__main__':
	MyApp().run()
```

What if when you wanted to build a GUI you could just use a **beautiful** DSL that makes sense and is clean? 

```python
<HomeScreen>:
	BoxLayout:
		orientation: 'vertical'
		size: root.width, root.height
		id: home
		counter: 0
		
		Label:
			id: label1
			text: 'Hello World!'

		Button:
			id: button1
			text: 'click me!'
			on_press: root.button_clicked()
```

What if when you wanted to run the application you just ran it without needing some emulator?

```shell
$ python main.py
```

What if when you wanted to deploy it you just connected your mobile and issued a few simple commands?

```shell
$ sudo apt-get install python-pip
$ sudo pip install buildozer
$ buildozer init
$ buildozer -v android debug deploy
```

What if for **kicks** you wanted to deploy to iOS?

```shell
$ buildozer -v ios deploy run
```

Well you don't _have_ to imagine, with Kivy and Python you can do this **today**. Doing things like accessing GPS is also just as effortless thanks to an high level API that does what all good API's should do which is **abstract away** the pain.

**Conclusion**

[Kivy](http://kivy.org/) is an amazing project for cross platform multi-touch GUI programming, Kivy is what I wanted mobile development to be like, simple straight forward and painless development and deployment. Although you can build some great apps this way and it may even be enough for cross platform development, it is still a hack.

**_So why did Google get mobile development so wrong?_** this comes to mind:

> Any intelligent fool can make things bigger, more complex, and more violent. It takes a touch of genius and a lot of courage to move in the opposite direction.(Albert Einstein)

One day mobile development tools may be like Kivy but native and without all the hacks, and when that happens it will be the new King of Hill and not because of muscle, it will be because developers will flock to it.