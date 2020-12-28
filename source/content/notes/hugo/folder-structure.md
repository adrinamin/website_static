---
title: "Playing around with Hugo static site generator"
sub_header: ""
date: 2020-11-28T19:11:32+01:00
tags: ["Hugo"]
draft: true
toc: false
---

I'm currently playing around with the static site generator Hugo lately. It's a very powerful static site generator, written in go. 

You have almost endless configuration options when creating hugo sites. In the beginning when you create a new site, you use the hugo CLI and type:

``
hugo new site <sitename>
``

## folder structure

* hugo lets define data about your content. This is defined in your **archetypes**

* **Content** folder contains all the markdown files

* **Data** folder acts as kind of a database. Here you can store data files like json. You can pull this data from your data file.

* **Layouts** folder defines the layout structure of your website

* **Static** contains all the images and stylesheets of your website

* **themes** is used for downloading and storing any hugo themes in here.

There is also a file called, **config.toml**. It is the settings file for your website. You don't have to use toml. You can also use YAML and JSON.