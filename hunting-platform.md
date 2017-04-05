---
layout: default
title: "Hunting Platform"
permalink: "/hunting-platform"
---
<h1>{{ page.title }}</h1>
We at the ThreatHunting Project are big fans of the analytic style of hunting, which involves writing code to sift through big piles of data to find the evil lurking within.  Our preferred hunting tool stack revolves around Python and [Jupyter Notebooks](http://jupyter.org).  If you've never used Jupyter before, think of a mixture of code, output and explanatory text, all in a single interactive document.  The notebook paradigm is ideal for the sort of interactive, hands-on work that goes into threat hunting, and at the end you have a record not only of your results, but (more importantly), of your _process_.  

One of the hurdles a new hunter often comes across, though, is figuring out what their analysis stack will be and then getting all the pieces to work together.  To make this a little easier, we've put together the imaginatively-named _Hunter_, a threat hunting/data analysis environment based on Python, Pandas, PySpark and Jupyter Notebook.  _Hunter_ packages high-performance Big Data analysis tools that can run on an individual laptop or as part of a VM hosted environment.  To help make it as easy as possible to get the stack up and running, we've assembled all the pieces into a Docker container so you can install and run the system with a single command.  

For most people who just want to _run_ Hunter, starting with the [Docker Hub page](https://hub.docker.com/r/threathuntproj/hunting/) would be best.  If you'd like to build the image yourself, or are just curious about the internals, the [GitHub page](https://github.com/ThreatHuntingProject/hunter) is where you'll want to be.

Feedback is welcomed and appreciated.  If you have problems, questions or comments, please visit the [GitHub page](https://github.com/ThreatHuntingProject/hunter) and use the "Issues" tab to get in touch.  You can also reach us on Twitter as @ThreatHuntProj.
