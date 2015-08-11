---
layout: post
title: "Adding Facebook App to Facebook Page"
description: "Adding your newly created Facebook app to your Facebook page"
category: Facebook
tags: [Facebook]
---

## The way before and how it changes

Before, every time we created an app, Facebook will automatically create an app page for our newly created app. But as they updated their API, they decided to remove the app page.

	https://developers.facebook.com/blog/post/611/

## The problem

Most of the time, we will need to add our app to a page. The way it was done before is by going to the app page and there will be an 'Add to Page' button on the page. But, since Facebook decided to remove it, there goes our convenience way.

Big apps get their own easier way to add, you can use Facebook's app directory search and there will be an option to add it to your page. 

To be listed in the directory automatically, your app will have to get at least 10 MAU or you can submit it manually and it will takes several days for it to be shown on the directory.

	https://developers.facebook.com/blog/post/2011/07/12/getting-your-apps-into-facebook-search-faster/

Buttt, sometimes we don't want our app to be added before its ready and to make it ready, we will have to test it with real Facebook page. Darn, why does it have to be this complicated.

## The Easy but Not so Conviniece Solution

As stated in Facebook's blog entry, to add our app manually, Facebook provides something called 'App Dialog' but you will have to manually code it in a HTML file

	https://developers.facebook.com/blog/post/611/

{% highlight html %}

<html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:og="http://ogp.me/ns#"
      xmlns:fb="http://www.facebook.com/2008/fbml">
<body>
  <a href="#" onclick=window.open("http://www.facebook.com/dialog/pagetab?
  app_id=YOUR_APP_ID&redirect_uri=YOUR_URL","PageTab","width=500,height=200");>
  Dialog</a>
</body>
</html>

{% endhighlight %}

My preferable way is to just use the direct link to add it. Yep, you will have to open or send a GET request to a certain link just to add your facebook app to a facebook page

	https://developers.facebook.com/docs/pages/page-tab-dialog

The link
	
	https://www.facebook.com/dialog/pagetab?app_id=YOUR_APP_ID&redirect_uri=YOUR_URL

`YOUR_APP_ID` : as stated, this is where you put your Facebook app ID
`YOUR_URL` : When the request succeeded, Facebook will redirect the browser to this URL, so I usually just use whatever

Access the link or send GET request with the right parameters and voila! the 'app dialog' will be shown and you can choose which page you want the Facebook app to be added.

## BUT WAIT!! That's not all!!

If you just create a Facebook Application and access the link directly, it won't work....
YEEESSSS, you think this will be a smooth journey but it never is with Facebook API.

So for your app to be able to be added to a Facebook page, it will have to have the right settings. Precisely, your app will have to support `Facebook Page Tab`

To achieve that,

	1. Go to your Application Dashboard
	2. Click 'Settings'
	3. Scroll to the bottom
	4. Click on the 'Add Platform' button
	5. Choose 'Page Tab'

And it will create a `Page Tab` settings in your application settings. For `Secure Page Tab URL` I just input whatever URL and change the `http` with `https` for first time, Facebook doesn't do any url checking on it.

AND FINALLY

You can now go to the link again to add your app to your page

	https://www.facebook.com/dialog/pagetab?app_id=YOUR_APP_ID&redirect_uri=YOUR_URL

Now, that sure is easy.