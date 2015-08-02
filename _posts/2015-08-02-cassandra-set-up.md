---
layout: post
title: "Cassandra set up in Mac"
description: "Cassandra set up in Mac"
category: Database
tags: [Cassandra]
---
{% include JB/setup %}

## What is Apache Cassandra

Its a database.

## Installing Cassandra on MacOSX

Assuming that you already installed homebrew, you can easily install it by using terminal

	brew install cassandra

And we'll need python for that so if you also haven't got that, then

	brew install python

And CQL for console query

	pip install cql

## Starting the server

There are 2 options, start it automatically on login or just now.
To see how, you can type

	brew info cassandra

And it will give you the command that you'll need. For example, if you want to start now

	launchctl load /usr/local/opt/cassandra/homebrew.mxcl.cassandra.plist 

## Query from terminal

	cqlsh

## Basic Queries

Create keyspace first

	CREATE KEYSPACE demo WITH REPLICATION = {'class': 'SimpleStrategy', 'replication_factor':1 };

Then use the keyspace

	USE demo

And just queries like all other SQL queries

## That's it!

Now you can bricked me for being lazy

## References
a.k.a hope its not dead yet links
a.k.a you should probably read these people blog instead of mine

http://christopher-batey.blogspot.com/2013/05/installing-cassandra-on-mac-os-x.html?m=1
http://www.planetcassandra.org/create-a-keyspace-and-table/