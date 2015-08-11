---
layout: post
title: "Facebook Page Subscribed Apps"
description: "Your Facebook Page Subscribed Apps"
category: Facebook
tags: [Facebook]
---	

## What the hell is this `Subscribed Apps`

Honestly, I don't know. There is a documentation for it but it doesn't even state what the hell is this `Subscribed apps`

	https://developers.facebook.com/docs/graph-api/reference/v2.4/page/subscribed_apps

But if you look at the older documentation (v2.2), there is some descriptions on this `subscribed apps`

	Subscribed Apps for a Facebook Page. This edge will allow you subscribe or unsubscribe an app to real time updates for a Page.

	Apps that are in development mode will not receive real time updates.

	A Page Access Token is required for all methods.

And, from my experience is, I'm using it to create a webhook from my Facebook Page to my application URL.
So Facebook will sent live updates from my Page to my application.

## View your page subscribed apps

I would reccomend using the 'Graph Explorer' tools for this. 

	developers.facebook.com > Tools & Support > Graph API Explorer

You will need to use 'Page Token' to make any request for `subscribed_apps` and that means you will need to have admin role in the page.

So, just choose `GET` request and use this url format

	{page_id}/subscribed_apps

If you use the right token and have the sufficient access to the page, it will show all your page subscribed apps.

## Add your app to your page subscribed_apps

So here goes the meat of the bussiness. To be able to receive live feeds from a page, my application will need to be added to the page's subscribed_apps.

We will be using the same url in the Graph Explorer with the page you want to subscribed to token.

	{page_id}/subscribed_apps

But instead of sending `GET` request, we will be sending `POST` request. So click on the `GET` dropdown and choose 'POST'

If you just send it like that, there will be no error but Graph API Explorer default application is `Graph API Explorer`. You will need to use your application to send the `POST` request. To do this

	1. Scroll to 'Graph API Explorer' title header
	2. There will be a 'Application' text with dropdown besides it
	3. Choose your application from the dropdown 

Now send the `POST` request again, still using the page you want to subscribed to token. There should be no error and when you send the same request using `GET`, your newly subscribed application should be listed.