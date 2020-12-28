---
title: "Getting a specific page in Hugo"
sub_header: ""
date: 2020-11-28T19:12:11+01:00
tags: ["Hugo","page"]
draft: true
toc: false
---

When using Hugo static site generator you can add specific content to your html. You can use the following function

``
{{ with .GetPage "/path/to/page.md" }}{{ .Title }}{{ end }}
``

In this case the title of your page is displayed in your html.