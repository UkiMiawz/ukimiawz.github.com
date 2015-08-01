---
layout: post
title: "Cassandra lib for Python"
description: "Cassandra lib for Python"
category: Database
tags: [Cassandra]
---
{% include JB/setup %}

## The Lib

Behold! The Github link

	https://github.com/datastax/python-driver

They got documentations and stuff, so its quite easy to use

## Example Usage

I'm trying this one from Flask

{% highlight python %}

import os
import time
import simplejson
from pprint import pprint
from flask import Flask, jsonify, request
from cassandra.cluster import Cluster

app = Flask(__name__)
localIp = '192.168.59.103'
cluster = Cluster([localIp], port=9042, protocol_version=3)

@app.route('/')
def hello_world():
    return 'Don\'t panic!'

@app.route("/cassandra")
def cassandra_test():
    session = cluster.connect("demo")
    cql = "SELECT * FROM users LIMIT 1"
    r = session.execute(cql)
    return str(r[0])

if __name__ == '__main__':
    app.run(debug=True, host="0.0.0.0", port=8001)

{% endhighlight %}
