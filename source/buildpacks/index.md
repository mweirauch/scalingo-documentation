---
title: Buildpacks
date: 04/01/2015
tag: buildpacks, build, image
category: internals
---

# Buildpacks

## Introduction

When you want to deploy your application on Scalingo, it needs to be build as
a portable container image. This image will be loaded by our servers to run
and scale your app.

A buildpack is a set of scripts which aims at:

* Detecting the language of an application `detect`
* Installing the dependencies of a project `compile`
* Defining how the application should be started `release`

## Buidpacks included on Scalingo

* `Ruby` — [Documentation](/languages/ruby) — [Source](https://github.com/Scalingo/ruby-buildpack)
* `Node.js / io.js / Meteor` — [Documentation](/languages/javascript/nodejs) — [Source](https://github.com/Scalingo/nodejs-buildpack)
* `PHP` — [Documentation](/languages/php) — [Source](https://github.com/Scalingo/php-buildpack)
* `Java` — [Source](https://github.com/Scalingo/java-buildpack)
* `Python` — [Source](https://github.com/Scalingo/python-buildpack)
* `Go` — [Source](https://github.com/Scalingo/go-buildpack)
* `Scala` — [Source](https://github.com/Scalingo/scala-buildpack)
* `Erlang` — [Source](https://github.com/Scalingo/erlang-buildpack)
* `Haskell` — [Source](https://github.com/Scalingo/haskell-buildpack)
* `Clojure` — [Source](https://github.com/Scalingo/clojure-buildpack)
* `Grails Framework` — [Source](https://github.com/Scalingo/grails-buildpack)
* `Play Framework` — [Source](https://github.com/Scalingo/play-buildpack)

## Use a custom buildpack

We want our users to be able to use the technologies they love, we try to provide the support for
an extended range of languages and frameworks, but if we don't fit your need, you can use a
[custom buildpack](/buildpacks/custom).

## Specify a precise buildpack

In some cases, your application may be detected by two different buildpacks, for instance if you
are building a PHP application which manages its dependencies with `grunt` tasks, `bower` or `gulp`,
your application will be detected as a NodeJS application and as a PHP application.

In this situation you need to specify the buildpack you want to use by defining the environment variable:

```
BUILDPACK_NAME=php
```

