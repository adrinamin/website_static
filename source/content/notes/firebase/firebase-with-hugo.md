---
title: "How to use Firebase to host a Hugo site"
sub_header: ""
date: 2021-01-04T13:18:18+01:00
tags: ["Firebase","Hugo"]
draft: false
toc: false
---

If you want to create a blog or a personal website, and you want to write your site using HTML, CSS and JavaScript, static site generators are a good way to create your site quickly.

In this quick tutorial, I want to show you:

1. **How to implement Firebase into your Hugo site**
2. **How to push your site to Firebase**
3. **How to implement the Firebase into your CI/CD using GitHub actions**

## Quick Explanation about Hugo and Firebase
I recently started to create my own web page. I wanted the page to only contain static content. Thus, I decided to use a static site generator. 

After looking for some site generators at [JAMstack](https://jamstack.org/generators/), I found [Hugo](https://gohugo.io/): A fast static site generator written in Go. It's been around for quite some time and it is very feature-rich. 

After creating my static website the main question was where to host the page. The Hugo documentation page offers tutorials for hosting a Hugo site to a variety of platforms including Firebase.

Firebase is a Backend-as-a-Service (BaaS) provided by Google. It supports multiple platforms like iOS, Android or Unity, and you can also host your web app or static website. It provides a free plan which is sufficient for smaller or personal projects (see the [pricing](https://firebase.google.com/pricing/)). 

To leverage the services from Firebase you only need a Google Account. Deploying a site can be done manually through the CLI or you can implement it into your CI/CD. 

## 1. How to implement Firebase into your Hugo site?

For this part, You should already have a running Hugo site. If not, check out the [Hugo Quick Start tutorial](https://gohugo.io/getting-started/quick-start/).

Firebase contains a CLI which you can install on your local machine using a _npm_, a _standalone binary_ or an _auto install script_ (see the [Firebase documentation](https://firebase.google.com/docs/cli/)). The Firebase CLI provides full capabilities to work with your resources.

### Create a new Firebase project

First of all, what is a Firebase project? Google describes it as follows:

> _When you create a new Firebase project in the Firebase console, you're actually creating a Google Cloud project behind the scenes. You can think of a Google Cloud project as a virtual container for data, code, configuration, and services. A Firebase project is a Google Cloud project that has additional Firebase-specific configurations and services._

Thus, keep in mind that Firebase is always directly connected to the Google Cloud.

For creating a new Firebase project you can either use the [Firebase console](https://console.firebase.google.com/) or you use the Firebase CLI:

* When using the Firebase console, you can create a new project at [https://console.firebase.google.com](https://console.firebase.google.com)

* Click on "Add Project" and go through the project creation process. It's pretty straight forward.

* After your project is created you can open your terminal and run the following command 

    `firebase project:list` 
    
    to list all your created projects.

### Initialize Firebase for your Hugo page 

Firebase provides an easy step-by-step process for setting up a Firebase project. In your Hugo project run the following command:

`firebase init`

A menu appears where you can select a Firebase feature. Here, you select  "Hosting".

Then the initialization process starts:

1. First, we choose the previously created project by selecting the menu point **_Use an existing project_**. If you haven't created a new Firebase project yet, you can create it with the Firebase CLI by running following command:

    `projects:create [options] [projectId]`

2. After that, you define which folder should be the public directory for your Firebase project. If you already navigated to the corresponding folder, just press enter. 

3. Firebase also wants to know whether your site should be configured as a single-page app. For our Hugo site you respond with "No". 

4. In the end, Firebase asks whether it should set up automatic builds and deploys with GitHub. Here Firebase creates YAML files which define your build and deployment scripts. It also connects to GitHub during this process and creates the necessary secrets for you. 
<br> If your repository is not hosted on GitHub, this has no benefit for you. Otherwise respond with "Yes". 

## 2. How to push your site to Firebase?

If you want to push your site to firebase manually, you can simply do it by running the following command:

`hugo && firebase deploy`

When running the `hugo` command, Hugo composes all your files and content together and generates your site for you. The generated site is saved inside a folder called **_public_**. If you set the public firebase directory correctly, firebase will deploy your site.  

## 3. How to implement the Firebase into your CI/CD using GitHub actions?

For those of you using a GitHub repository: When you let Firebase create GitHub actions workflow files, you have two generated YAML files inside your .github/workflows folder:

* firebase-hosting-merge.yml
* firebase-hosting-pull-request.yml

The names of those files might vary for you. The content of both files is the same. To make it work properly with Hugo, I adjusted the workflow a little bit.

{{< gist adrinamin f830ea9a65957e99be6d17af04bf6be8 >}}

Notice that I divided everything in separate steps to have a better overview of the entire process. 

I set up Hugo with the action [peaceiris/actions-hugo](https://github.com/peaceiris/actions-hugo). The build step afterwards runs the command

`hugo --minify`

Here, your page is generated by Hugo. We also add the `--minify` option to decrease the file sizes of any supported output format. If you need to change the working directory, do so with the `working-directory` keyword. The rest of the script can remain as generated by the Firebase CLI.

## Conclusion

Hosting your static site on Firebase is straight-forward and easy. You can host your site in minutes on Firebase and the free plan is sufficient for smaller to medium workload. Just keep in mind to adjust the generated workflow files for Hugo, otherwise the script might not work out of the box.


