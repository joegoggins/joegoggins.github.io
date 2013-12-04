---
layout: post
title: "Controlling a Spark Core remote control car with a bash script"
date: 2013-12-04 01:14
comments: true
categories: SparkCore
---

I just wrote a bash script to control a Spark Core powered remote control car over the internet. Hit "f" to go forward, hit "b" to backward, etc. Kinda sweet.

I grabbed the [RC Car Spark Core firmware code](http://docs.spark.io/#/shields), compiled it + flashed it to the core over USB by following [these instructions](https://github.com/spark/core-firmware). Essentially, I replaced the src/application.cpp with the code from the site and ran `make clean dependents all`, then used dfu-util to flash it.

I wrote up this script to make interacting with this simple Spark Core program a little less cumbersome, to use at the [Tinkerer's Ball](https://www.facebook.com/events/1422886744594947/) at the Science Mueseum this Thursday, and also for folks who are looking for something minimal to wrap up curl commands that they are throwing at the Spark Cloud API to talk to their Spark Core firmware program.

[Here's a short vid of me getting jazzed about this with my nasty mustache](https://vimeo.com/80969794) (This is a hangover from Spark's wonderous partaking in [Movember](http://us.movember.com/team/1217549).  Someone kill that thing! It's 4 days into December man!)

The idea of this bash script is to set SPARK_CORE_DEVICE_ID and SPARK_CORE_ACCESS_TOKEN, then run a pre-defined function that loops for input and translates that [Spark Cloud API](http://docs.spark.io/#/api) curl commands. Please fork or comment if applicable.

{% gist 7777824 %}
