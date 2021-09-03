---
title: "Frequently used Hugo variables"
sub_header: ""
date: 2020-11-29T13:21:00+01:00
tags: ["Hugo"]
draft: true
toc: false
---

In general you access variables with open and closed curly braces.

Here is a list of the most important variables which I frequently used:
* .Title
* .Date
* .Permalink
  
We can also access custom variables from our front matter:
* Params.myCustomVar

We can create custom variables as well:

``
{{ $string := "hello" }}
{{ $string }}
``