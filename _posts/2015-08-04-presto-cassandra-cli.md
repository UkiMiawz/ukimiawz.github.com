---
layout: post
title: "Presto with Cassandra CLI"
description: "Presto with Cassandra CLI"
category: Database
tags: [Cassandra, Presto]
---

## What is Presto

Its a connector between different databases (Cassandra, MySQL, etc)

## Official Documentation

To set the server up on your local machine, please read the official documentation
Its a simple and step-by-step guide

https://prestodb.io/docs/current/installation/deployment.html

## Cassandra connector

To create a cassandra connector, you need to create `cassandra.properties` file in your `catalog` folder
This is what I have in my `cassandra.properties`

	connector.name=cassandra
	cassandra.contact-points=192.168.59.103

`192.168.59.103` is my cassandra server host

## Set config.properties

On `config.properties` file, change `discovery.uri` value to a host address, this will be the address that Presto server hosted at
	
	discovery.uri=http://localhost:8080

## Run the server

You can run the server by using

	bin/launcher run

or

	bin/launcher start


The `run` one will listen to the port and print out logs. If your presto server alread up and running, you can try browsing to your presto host. In my case, its `http://localhost:8080`. You will see page with presto logo and it will updates live with presto server logs.

## Connect with Presto Cli

You will need to download Presto executable Jar

	https://prestodb.io/docs/current/installation/cli.html

To connect with our cassandra database through presto server, I use this command

	./presto.jar --server localhost:8080 --catalog cassandra --schema default

It will connect to your Cassandra `default` keyspace.

## Switch keyspace and query

You are now inside your Cassandra server and can query as usual.

	USE my_keyspace
	DESCRIBE my_tables

