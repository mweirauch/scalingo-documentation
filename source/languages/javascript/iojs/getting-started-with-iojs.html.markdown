---
title: Getting started with io.js
category: languages
date: 09/02/2015
tags: programming, dev, iojs, javascript, language, tutorial
---

# Getting started with io.js

## Initialize your application

```bash
$ mkdir iojs-app
$ cd iojs-app
$ npm init

# 
# You need to fill the different info field for your project
#

$ npm install express --save
$ echo "node_modules" > .gitignore
```

## Write a base server file

server.js

```js
// NodeJS - Express Sample application

var express = require('express')
var app = express()

app.get('/', function (req, res) {
  res.send('Hello World!')
})

var server = app.listen(process.env.PORT || 3000, function () {
  var host = server.address().address
  var port = server.address().port
  console.log('App listening at http://%s:%s', host, port)
})
```

<blockquote class="tip">
  The `process.env.PORT` will read the environment variable PORT dynamically provided by our container manager.
</blockquote>

## Define how to start your application

Procfile

```yml
web: iojs server.js
```

## Define io.js as javascript engine

In your `package.json`, add the following block:

```js
"engines": {
  "iojs": "1.1.x"
}
```

This will instruct the deployment scripts to install iojs at
the given version instead of Node.js

## Commit your application 

```bash
$ git init
$ git add .
$ git commit -m "Base io.js application"
```

## Create your application on Scalingo and deploy

<blockquote class="info">
  You can also use our web dashboard to achieve this operation
</blockquote>

```bash
$ scalingo create iojs-app
Git repository detected: remote scalingo added
→ 'git push scalingo master' to deploy your app

$ git push scalingo master
```

## Access your application

```
…
Waiting for your application to boot... 
<-- https://iojs-app.scalingo.io -->
```

Now develop your project and build something amazing!
