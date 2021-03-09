---
title: The Joys Of Migrating From SQL Server To MariaDB
author: zen master
type: post
date: 2014-06-02T08:00:27+00:00
url: /the-joys-of-migrating-from-sql-server-to-mariadb/
dsq_thread_id:
  - 2728604364
categories:
  - Articles
  - Tutorial
tags:
  - GUID
  - MariaDB
  - Migration
  - MSSQL
  - MySQL

---
**Introduction**

In my professional line of work I live within the full Microsoft stack. While there is nothing inherently wrong with this, the world is full of other stacks. I have to admit that Microsoft&#8217;s development tooling is top notch, its easy to get spoilt in that environment. However when it comes to pricing, freedom and platform independence then Microsoft is perhaps not the best choice.

Outside of work I do freelance development for a few customers. Freelancing give me the opportunities to use whatever stack I want. I&#8217;ve used a variety of languages on different jobs, whatever best suited the problem, everything from python to php.

![Data Migration][1]

One particular system I built was full on Microsoft stack, C# WinForm front end with your basic SQL Server Express backend store. Over the years the application has evolved, and recently the decision was made to convert it into a web application.

I didn&#8217;t think twice and started work on a asp.net front end, gutting out the old application and creating light weight web services.

The requirements had shifted for the application from providing for a single company, to potentially multiple companies. In terms of hosting, licensing and data growth etc staying with Microsoft was going to be expensive in the long term.

Part way through I made the decision that I needed to switch stacks. After doing a lot of research, I finally settled on using old school JSP and Java Servlets for the middle, and MariaDB for the back end store.

The front end was trivial to move over because it was just html css and js, the middle logic was just a matter of porting C# to Java. The only real challenge was going to be the database because of my heavy use of Stored Procedures.

I love stored procedures, I&#8217;m a die hard fan of them. However when it comes to migration this love can soon turn into hatred. I knew this part would be problematic ahead of time, so I decided that while porting I’d move the logic into the application layer away from the datastore so that in future the datastore can be vendor agnostic.

Stored procedures aside, the schema and data migration was in theory supposed to be the “simple” part.

Oh how wrong I was! I used Oracles Workbench data migration wizard to do the heavy lifting. Everything would have been a complete breeze, if if wasn&#8217;t for one small annoying problem: GUIDs!

Yes along with stored procedures, I also love GUIDS. In SQL Server GUIDs when used correctly work amazingly well. MariaDB doesn&#8217;t support them natively, so SQL Workbench simply imports these columns as VARCHAR(64).

In SQL Server if you use GUIDS as primary keys you can use the “NEWSEQUENTIALID()” default which creates sequential GUIDS which dramatically reduces index fragmentation. This is somewhat similar to UUID Version 1 in the MariaDB world.

After some digging around on the various forums and stackoverflow, the best choice for storing GUIDs in MySQL seemed to be BINARY(16). The only caveat was a bit of hexing and unhexing that was needed between storing and retrieving them.

I poked around SQL Workbench’s wizard to see if I could create a custom mapping, but alas it only allowed very simple data type changes. This was turning out to be an exercise in frustration :(

**Python to the rescue!**

It become clear that some manual intervention would be required to fix these GUID columns. Of course I could have knuckled down and gone through each column and converted them by hand. This naturally is not the way of the programmer! why do something manual when it can be automated?

The idea was dead simple use python to get the database schema, based on this meta generate the sql to do the actual transform. A little bit of debugging later I had a working sql script generator. Running the script against the newly migrated database ran within seconds and fixed up all the columns into BINARY(16) and created the primary keys when needed.

If you have find yourself in need pf cleaning up MSSQL GUIDs after a migration to MySQL or MariaDB then I’ve put my script up on [GitHub](https://github.com/Coding-Ninja/mssql-guid-transform)




**Conclusion**

Migrating databases in most cases will involve some amount of pain, automation tools are your friend but don’t believe the marketing hype. The tools will only get you most of the way. But to finish the job use the force of a scripting language to slay any nasty database dragons!

 [1]: http://i.imgur.com/7b2X9m6.jpg