---
layout: post
title: "Setting up GitHub in Windows"
description: "Setting your github"
category: github
tags: [github]
---
{% include JB/setup %}

## 1. Create Account
Create your account in <a href="http://www.github.com" target="_blank">Github</a>

##2. Install and Set up Git
Follow the steps in <a href="https://help.github.com/articles/set-up-git" target="_blank">Set up Git</a>. This will install gitbash to connect to your git repository in github

##3. Create SSH-Key
Before continue creating a repository, you should first create a SSH-Key. Follow these steps : <a href="https://help.github.com/articles/ssh-key-setup" target="_blank">Setting up SSH-Key for Git</a>. Don't forget to test your SSH-Key.

##4. Setting SSH-Agent
Git will ask for your passphrases everytime you used your SSH-Key. You don't like it? You can add a `.profile` file in your bash root and add some codes to run `ssh-agent`. This agent will allow you to enter your passphrases only once upon running bash.
You can find those codes here : <a href="https://help.github.com/articles/working-with-ssh-key-passphrases" target="_blank">SSH-Agent setting</a>

##5. Create Repository
Once you got your SSH-Key running smooth, you can start <a href="https://help.github.com/articles/create-a-repo" target="_blank">Creating repository</a>

	Attention :
	If you want to create a page with username.github.com, you should make a repository named 'username.github.com'. This kind of page called `user page`

	Git only allowed a page with your username, it will automatically recognized it as 'username.github.com' page and published it as user page. If you use something else other than username, git will recognized it as a project and you won't be able to publish `projectname.github.com`

	Example : My username is UkiMiawz, I tried to create potatogrammer.github.com page, so I (idiotically) create a repository named `potatogrammer.github.com`. Github recognized it as a project and instead of getting a `potatogrammer.github.com` page, I got a project page for it. HAHA! OTL

##6. Fork Repository
Once you create a repository, you can start managed it from your local by forking your repository. Once you're forked, you can push and pull changes to and from your repository. <a href="https://help.github.com/articles/fork-a-repo" target="_blank">Forking your repository</a>.

##Confused?
No worries, Git provided a help page, don't forget to check it
<a href="https://help.github.com/" target="_blank">Github Help Page</a>

And do some `Googling`
