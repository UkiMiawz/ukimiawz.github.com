---
layout: post
title: "Comitting changes to git repository"
description: "Comitting changes to git repository"
category: github
tags: [github, repository]
---
{% include JB/setup %}

Putting in here since I always forgot and too lazy to open the official web reference
Original page : <a href="https://help.github.com/articles/create-a-repo" target="_blank">Creating a repository</a>

##For new repository, create and init local folder

		$ mkdir ~/Hello-World
		# Creates a directory for your project called "Hello-World" in your user directory
		
		$ cd ~/Hello-World
		# Changes the current working directory to your newly created directory
		
		$ git init
		# Sets up the necessary Git files
		# Initialized empty Git repository in /Users/you/Hello-World/.git/
		
		$ touch README
		# Creates a file called "README" in your Hello-World directory

##Create a remote for comitting changes

		$ git remote add origin git@github.com:username/Hello-World.git
		# Creates a remote named "origin" pointing at your GitHub repo

For my page, the line will be
	
		$ git remote add origin git@github.com:UkiMiawz/ukimiawz.github.com.git

		Attention: Eventhough your username in page is not case sensitive, your username is.
		I got a 'repository not exist' error several time just because I (foolishly)
		write my username as 'ukimiawz' instead of 'UkiMiawz'

##Add and commit

Add changes
	
		$ git add .
		# There's a '.' in the end of the line

If you delete any files, you will need to add '-A' in the end of the command line or the files won't be deleted from your repository

		$ git add . -A
		# There are files deleted

Commit changes to repository

		$ git push origin master

##Pull changes

Add upstream to fetch changes from repository

		$ git remote add upstream git://github.com/username/repository.git

For my page it will be

		$ git remote add upstream git://github.com/UkiMiawz/ukimiawz.github.com.git

		Attention: Eventhough your username in page is not case sensitive, your username is.
		I got a 'repository not exist' error several time just because I (foolishly)
		write my username as 'ukimiawz' instead of 'UkiMiawz'

Fetch changes

		$ git fetch upstream

##Mergering changes

Should you received command upon commiting to merge your changes with your existing files in repository, you should fetch changes and merge it with your local

		$ git merge upstream/master
