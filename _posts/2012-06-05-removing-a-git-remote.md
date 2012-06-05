---
layout: post
title: "Removing a git remote"
description: "Removing a git remote"
category: github
tags: [github, remote]
---
{% include JB/setup %}

Full post in here : <a href="https://help.github.com/articles/removing-a-remote" target="_blank">Removing a Remote</a>

##To check your current remote

		$ git remote -v# View current remotes
		# origin  git@github.com:user/repo.git (fetch)
		# origin  git@github.com:user/repo.git (push)
		# destination  git@github.com:forker/repo.git (fetch)
		# destination  git@github.com:forker/repo.git (push)
		
##Remove a remote

		$ git remote rm destination
		# Remove remote

##Check your remote again to verify

		$ git remote -v# Verify removal
		# origin  git@github.com:user/repo.git (fetch)
		# origin  git@github.com:user/repo.git (push)

