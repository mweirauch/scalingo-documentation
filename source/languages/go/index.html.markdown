---
title: Go
category: languages
date: 22/12/2014
tags: programming, dev, go, language
---

# Go

The Go programming language is supported.

## Deploying a Go application

### Using Godeps

When deploying a go application it is important to ensure that the
compilation is completely reproducible.  Godeps ensures this by vendoring
all the third-party dependencies of your project in the `Godeps/_workspace`
directory of your project.

#### Setting up Godeps

```
go get github.com/tools/godep
godep save <package of your project>
git add Godeps
git commit -m "Vendor all dependencies with Godeps"
```

For more details about the management of these vendored dependencies,
refer to [the Godeps documentation](https://github.com/tools/godep).

#### Defining a Procfile

```
web: <package name>
```

You can find an example at: https://github.com/Scalingo/sample-go-martini

### Using .godir (Deprecated)

The alternative is to use a `.godir` file a the root of your project
defining the name of your project binary. All the dependencies will be
downloaded using `go get` and in this case the repeatability of the
operation is not ensured.

`.godir`:
```
my-sample
```

`Procfile`:
```
web: my-sample
```

Example: https://github.com/Scalingo/sample-go-martini/tree/godir

## Buildpack

[Link to Go Buildpack](https://github.com/kr/heroku-buildpack-go)
