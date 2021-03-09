---
title: Export osTicket to Atlassian Jira Service Desk
author: zen master
type: post
date: 2015-03-04T11:11:21+00:00
url: /export-osticket-to-atlassian-jira-service-desk/
dsq_thread_id:
  - 3566111551
categories:
  - Uncategorized
tags:
  - Export
  - JIRA
  - JSON
  - osTicket

---
**Introduction**

Our old ticket system (**osTicket**) has served us well. However the time had come to move them onto Atlassian's **JIRA** service desk. While JIRA seems to have many different import mechanism it didn't have an option to import from osTicket.

Our version of osTicket didn't have an export option (or at least I could not find it). JIRA does have the option to import via JSON format.

So I've decided to put this out there in the wild **just** in case that some else might need such a thing.

**Github:**

https://github.com/Coding-Ninja/osTicketExporter