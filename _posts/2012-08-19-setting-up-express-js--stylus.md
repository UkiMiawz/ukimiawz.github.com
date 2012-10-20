---
layout: post
title: "Setting up Express JS & Stylus"
description: "Starting up with Express JS & Stylus"
category: Node JS
tags: [Node JS, Express, Stylus]
---
{% include JB/setup %}

Some goody goody tutorial:
http://howtonode.org/express-mongodb

##Install Express JS

		// You may need to run this under sudo
		npm install express -g

##Create a directory

	mkdir testing

##Move and point to directory

	cd testing

##Set up directory to default
	
	express -c stylus
	npm install -d

This should be enought to start a basic application. What have been done : (quoting from how to node)
1. Made the blog directory for your project (might be a good idea to put this under source control)
2. Asked express to generate an application using the jade template engine and the stylus css engine (jade is the default html template engine)
3. Asked npm to download and locally install any dependencies required by this express application

##Test the installation
	
	node app.js
	
The basic application should be started when you browser `localhost:3000`
