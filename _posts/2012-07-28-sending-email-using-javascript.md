---
layout: post
title: "Sending Email Using Javascript"
description: "Sending Email Using Javascript Node Mailer"
category: Javascript
tags: [Javascript]
---
{% include JB/setup %}

For my latest project, I was having some mail forwared development using Javascript. Luckily for Node JS we already got some fancy easy to use library.

We're using `Marak Node Mailer` for the project, you can check it on Github

<a href="https://github.com/Marak/node_mailer" target="_blank">https://github.com/Marak/node_mailer</a>

and you can use npm to install it, don't forget to install the latest version

	npm install nodemailer@latest

## Code Jumble

Here's some usage example, I'm using SMTP for this example. You can check more example at their site
<a href="http://documentup.com/andris9/nodemailer/" target="_blank">Nodemailer documentations</a>

	// JavaScript Document
	var nodemailer = require("nodemailer");

	var transport = nodemailer.createTransport("SMTP", {
	    host: "smtp.yourhost.com", // hostname
	    secureConnection: false, // use SSL
	    port: 123, // port for secure SMTP
	    auth: {
	        user: "username",
	        pass: "password"
	    }
	});

	transport.sendMail({
	    from: "test@somemail.com",
	    to: "testto@somemail.com",
	    subject: "Test SMPT Mail using NodeJS Mailer",
	    text: "Tralalalallala"
	}, function(error, responseStatus){
	    if(!error){
	        console.log(responseStatus.message); // response from the server
	    }
	});
