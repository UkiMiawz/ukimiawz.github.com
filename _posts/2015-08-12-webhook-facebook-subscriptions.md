---
layout: post
title: "Webhook for Facebook with Subscriptions"
description: "Webhook for Facebook with Subscriptions"
category: Facebook
tags: [Facebook]
---	

## The Problem

So, I need to record feed (comments, like, posts) from my Facebook Page and record it to my database.
I will need to use `Facebook Graph API Real Time Updates` for this.

Official documentation

	https://developers.facebook.com/docs/graph-api/real-time-updates/v2.4

But as always, deciphering Facebook's documentation is a form of art.

## Create a Facebook application

You will need Facebook app ID and secret key to create a permanent token for the feed. This link will help you.

	https://developers.facebook.com/docs

## Add your app to your page's subcribed apps

To receive live updates from your Facebook App, you will need to add your app to your page's subcribed apps.

Refer to previous entry for steps

	http://ukimiawz.github.io/facebook/2015/08/11/facebook-page-subscribed-apps/

## Create a Callback URL

You will need to create a page in your server. This page will serve as a receiver for facebook JSON live updates. The tricky part is, this page will need to support both `GET` and `POST` request from facebook.

On subscribing, facebook will send a `GET` request to your callback url with several parameters.

	hub.mode - The string "subscribe" is passed in this parameter
	hub.challenge - A random string
	hub.verify_token - The verify_token value you specified when you created the subscription

You will need to verify the token to make sure that it's Facebook that made the requests.
You will also need to print out `hub.challenge` parameter value to your page. 

In python :

	request.args.get('hub.challenge', 'default-value') 


Or just for testing, you can create a temporary callback url at `RequestBin`
	
	http://requestb.in/

## Send a Subscribe request to the page

Lastly, you will need to send `POST` request for the subscriptions

	https://developers.facebook.com/docs/graph-api/reference/v2.4/app/subscriptions/

Using the `Graph API Explorer` might be the easiest way and the url format is

	/{object-id}/subscriptions

This `object-id` is your page ID if you want to receive live updates from your page. You will need to send some parameters along the `POST` request

	- object
	Indicates the object type that this subscription applies to.
	enum{user, page, permissions, payments}

	- callback_url
	The URL that will receive the POST request when an update is triggered.
	string

	- fields
	The set of fields in this object that are subscribed to.
	string[]

	- active
	Indicates whether or not the subscription is active.
	bool

For the valid fields options, you can check more in here on `Valid Fields for Subscription`

	https://developers.facebook.com/docs/graph-api/real-time-updates/v2.4

You can send several fields if you want to receive updates from several parts of the pages (name, description, etc) But I usually just use `Feed`.

`Feed` will sent you updates on your Facebook Page's comments, likes, and new posts.

