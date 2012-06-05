---
layout: post
title: "Node JS Cannot find module 'formidable'"
description: "Node JS Cannot find module 'formidable'"
category: NodeJS
tags: [NodeJS, module]
---
{% include JB/setup %}

In my recent project I got this error upon trying to use `formidable` module in NodeJS.

		Cannot find module 'formidable'

The funny thing is that module does exist since I just installed it using NPM a moment before.

It turns out I need to update the formidable module to it's latest by using this command

		npm install formidable@latest