---
title: "Composition for better testability?"
sub_header: ""
date: 2021-04-01T13:18:18+01:00
tags: ["code quality","testing","clean code"]
draft: false
toc: false
---

How many times did you want to test a class which inherits another class? Probably quite often. And how often did some property or method from the base class your life pretty difficult because you couldn't test the actual system under test? I guess quite often as well.

 Inheritance is not bad in general but sometimes in the object-oriented paradigm, you'll find big hierarchy structures which make testing almost impossible.

Of course, good software architecture and design avoid those scenarios. Today I want to look at one best practice, called "favor composition over inheritance" which untangles those hierarchy structures in your application. For that I want to discuss the following points:

* What's wrong with inheritance
* What does composition even mean
* How to implement this best practice with .NET
* How does it help with the testability of your app

Read the full post at [codequality.rocks](https://www.codequality.rocks/post/favor-composition-over-inheritance)!