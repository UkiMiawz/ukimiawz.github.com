---
layout: post
title: "What The Hell is Jekyll"
description: "What is Jekyll"
category: Jekyll
tags: [Jekyll]
---
{% include JB/setup %}

For those who confused of what jekyll is (like me), here are some points to node about Jekyll :

##1. It is not a CMS
You might have experience using CMS like Wordpress, Joomla, Blogspot, Tumblr or whatever. Eventhough Jekyll can be used to produce blogs, it it not a CMS.

##2. Jekyll is a simple, blog aware, static site generator.
And what the hell is static site generator?? Quoting from Nettuts : A static site generator is a program that takes a set of files and generates your site with them. Basically, you create files, give it to Jekyll, and it will generate your files into static web pages.

##3. You won't get any pretty administration page
It is simply a generator, Jekyll do not provide administration page, fancy or not. You will need to code down your posts and templates.

##4. Jekyll saves posts as `.md` files
You can edit this MD files and add your content in it. For example, this is some part of my `.md` file

		---
		layout: post
		title: "The Hell is Jekyll   Using Jekyll to generate your site"
		description: "Using Jekyll"
		category: Jekyll
		tags: [Jekyll]
		---
		{% include JB/setup %}

		For those who confused of what jekyll is (like me), here are some points to node about Jekyll :

		##1. It is not a CMS
		You might have experience using CMS like Wordpress, Joomla, Blogspot, Tumblr or whatever. Eventhough Jekyll can be used to produce blogs, it it not a CMS.

You can see the file got title, description, category and tags. Looks familiar?

##5. IT IS VERY FAST
The reason I tried using Jekyll is purely for fun and experimental. But it turns out pages build using Jekyll is very fast loading. Unlike wordpress or Tumblr that sometimes took forever to load, Jekyll simply creates static pages which very fast loading. Creating posts and pages is also very fast since you won't need to wait for any backend blog administration loading.

##6. You will need basic HTML knowledge for using Jekyll
Since there won't be any fancy text-editor, you will need to code your posts including all the HTML tags by hand. This might be challenging for those who don't have any HTML knowledge.

Nettuts+ got an excellent example for using Jekyll, you should check it out
<a href="http://net.tutsplus.com/tutorials/other/building-static-sites-with-jekyll/" target="_blank">Building Static Sites with Jekyll</a>

##Using Image in Jekyll

For example you got a folder name `img` and store your image there, instead of using `img\image.jpeg`, you will need to add `\` in front.

		<img style="background:#000000" src="/img/fontSquirell.png" alt="fontsquirrel" />