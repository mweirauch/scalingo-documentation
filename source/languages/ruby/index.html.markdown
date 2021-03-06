---
title: Ruby
category: languages
date: 17/10/2014
tags: programming, dev, ruby, language
---

# Ruby

Ruby is entirely supported by Scalingo, furthermore, custom support is added
for the Rails framework in all its versions.

* [Getting Started with Rails](/languages/ruby/getting-started-with-rails.html)

## Buildpack

The buildpack is based on `bundler` and will install the dependencies defined
in the `Gemfile` and `Gemfile.lock` of your project. ([source of the
buildpack](https://github.com/Scalingo/heroku-buildpack-ruby))

## Ruby application

### Ruby app detection

Presence of a `Gemfile`

## Rack based application

### Rack app detection

Presence of a `config.ru`

### Rack environment

When a rack application is detected, the following environment variable will be set:

* `RACK_ENV` → `production`

## Rails application

### Rails app detection

#### Rails 2

Presence of a `config/environment.rb`

#### Rails 3, Rails 4

Presence of a `config/application.rb`

### Rails environment

* `RACK_ENV` → `production`
* `RAILS_ENV` → `production`

## Specifying a custom ruby runtime

If your need to install a custom version of ruby, you can achieve that by specifying
it in your Gemfile:

### Ruby MRI 2.1.3

```ruby
ruby "2.1.3"
```

### JRuby 1.9.3

```ruby
ruby "1.9.3", :engine => "jruby", :engine_version => "1.7.8"
```
