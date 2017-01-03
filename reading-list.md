---
layout: default
title: "Annotated Reading List"
permalink: "/reading-list"
---
<h1>{{ page.title }}</h1>
For those new to threat hunting, the ThreatHunting Project provides the following reading list to help you get started learning about the process.  

## Articles (Quick Start)

**[Incident Response is Dead... Long Live Incident Response](https://sroberts.github.io/2015/04/14/ir-is-dead-long-live-ir/)**, *Scott Roberts*

Straight talk in plain language about the idea of hunting, why your organization should be doing it, and what it takes to create a successful hunting program. Read this one first!

**[Demystifying Threat Hunting Concepts](https://medium.com/@jshlbrd/demystifying-threat-hunting-concepts-9de5bad2d818)**, *Josh Liburdi*

A strategic look at the importance of good beginnings, middles and ends of the hunt.  

**[A Simple Hunting Maturity Model](http://detect-respond.blogspot.com/2015/10/a-simple-hunting-maturity-model.html)**, *David J. Bianco*

Proposes a practical definition of "hunting", and a maturity model to help explain the various stages of hunting capability an organization can go through.  The HMM can be viewed as a roadmap that an organization can use to describe their current capability and plan for improvement.

**[The Threat Hunting Reference Model Part 2: The Hunting Loop](http://blog.sqrrl.com/the-threat-hunting-reference-model-part-2-the-hunting-loop)**, *Sqrrl*

Building on the HMM, this describes the hypothesis-driven cycle that successful hunters must iterate through

**[The Who, What, Where, When, Why and How of Effective Threat Hunting](https://www.sans.org/reading-room/whitepapers/analyst/who-what-where-when-effective-threat-hunting-36785)**, *Robert M. Lee & Rob Lee, The SANS Institute*

A very comprehensive discussion of many aspects of hunting, which a special emphasis on how it fits within the overal security program and the "active cyber defense cycle".

**[Generating Hypotheses for Successful Threat Hunting](https://www.sans.org/reading-room/whitepapers/threats/generating-hypothesis-successful-threat-hunting-37172)**,
*Robert M. Lee & David J. Bianco*

An in-depth discussion of the different types of hunting hypotheses and how to create good ones to get your hunts started right.

**[Building Threat Hunting Strategies with the Diamond Model](http://www.activeresponse.org/building-threat-hunting-strategy-with-the-diamond-model)**, *Sergio Caltagirone*

The first part of this article is all about how to organize and prepare for your next hunt.  It introduces "the 4 hunting questions" you must answer before you begin.  The second part presents a framework for categorizing different hunting approaches based on the [Diamond Model of Intrusion Analysis](http://www.activeresponse.org/wp-content/uploads/2013/07/diamond.pdf) (of which Mr. Caltagirone was a primary author).  

**[Cyber Threat Hunting (1): Intro](https://cyber-ir.com/2016/01/21/cyber-threat-hunting-1-intro/)**, *Samuel Alonso*

Another good intro to threat hunting. Offers a slightly different viewpoint on hunting than some of the other items in this list.

**[Cyber Hunting: 5 Tips to Bag Your Prey](http://www.darkreading.com/risk/cyber-hunting-5-tips-to-bag-your-prey/a/d-id/1319634)**, *David J. Bianco*

Who doesn't like a good "Top N" list??  This one offers 5 quick bullet points to help you think about how to get your team started hunting.

**[Threat Hunting: Open Season on the Adversary](https://www.sans.org/reading-room/whitepapers/analyst/threat-hunting-open-season-adversary-36882)**, *Dr. Eric Cole, The SANS Institute*

The recent SANS threat hunting survey is probably the most authoritative source on how real practitioners and security executives view hunting, their own hunting programs, and their wants & needs for improvement.  

## Books

**[Data-Driven Security: Analysis, Visualization and Dashboards](https://www.amazon.com/Data-Driven-Security-Analysis-Visualization-Dashboards/dp/1118793722)**, *Jay Jacobs & Bob Rudis*

A wide-ranging look at many aspects of data analysis and presentation fundamental to many hunting techniques.  Includes lots of code in R, but also Python.  It's great for learning the basic ideas behind data analysis and using the results to make decision and drive changes in your security program.  

**[Network Security Through Data Analysis: Building Situational Awareness](https://www.amazon.com/Network-Security-Through-Data-Analysis/dp/1449357903)**, *Michael Collins*

Covers many (free!) tools for collecting and analyzing large amounts of data, primarily to find potential intrusions.  The book takes a heavily hands-on, practical approach with extensive examples written in Python.  

## Other Resources

**[Windows Commands Abused by Attackers](http://blog.jpcert.or.jp/.s/2016/01/windows-commands-abused-by-attackers.html)**, *JPCERT/CC*

Using data drawn from actual attacks, this article shows the most common Windows commands used and abused by attackers once they gain access to a system.  The commands are organized into "Initial Investigation", "Reconnaissance" and "Spread of Infection" (Lateral Movement).  There are no actual analytic techniques discussed here, but the data will be quite useful as the basis for generating some hunts based on Windows command usage.
