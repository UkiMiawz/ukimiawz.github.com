---
layout: post
title: "Git Jekyll Commands"
description: "Git Jekyll usefull commands list"
category: Jekyll, Github
tags: [Jekyll, Command, Github]
---
{% include JB/setup %}

##Create Server

		$ jekyll --server

##Create Post

		$ rake post title="Hello World"

##Create Page

		$ rake page name="about.md"

Nested page

		$ rake page name="pages/about.md"

Rake page with pretty path

		$ rake page name="pages/about"
		# this will create the file: ./pages/about/index.html

##Installing Theme

From URL

		$ rake theme:install git="https://github.com/jekyllbootstrap/theme-the-program.git"

From local folder

		$ rake theme:install name="THEME-NAME"

##Switch Theme

		$ rake theme:switch name="the-program"
		# for 0.1.0 users `rake switch_theme` still works.

#After Customize

In order to see changes, you will need to switch again

		$ rake theme:switch name="the-program"
