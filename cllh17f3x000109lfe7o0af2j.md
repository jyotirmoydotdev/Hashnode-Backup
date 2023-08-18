---
title: "Use Gin Web Framework to build your server"
datePublished: Fri Aug 18 2023 20:17:05 GMT+0000 (Coordinated Universal Time)
cuid: cllh17f3x000109lfe7o0af2j
slug: use-gin-web-framework-to-build-your-server
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692389762409/ed30ba2f-f362-4d26-8cf3-34edec92a159.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692389802422/6fbd9942-52cb-4d99-962d-947c04acf4d3.jpeg
tags: server, golang

---

Let's build a simple web service using the Go programming language and the Gin web framework. We will define a basic web server that listens for incoming HTTP requests and responds with JSON data. The application would have a modular structure with separate files for the main application logic (`Main.go`), route handling (`web/Router.go`), and a specific route handler (`web/Assignments.go`).

```bash
├── go.mod
├── go.sum
├── main.go
└── web
    ├── assignments.go
    └── router.go

2 directories, 5 files
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">To create this structure in your terminal, utilize the 'tree' package. If you're on a Mac, employ the command 'brew install tree' and execute the 'tree' command. This will generate the desired output structure.</div>
</div>

# Setup

Create a folder **learn-Gin** and inside it make an empty file **main.go**. After that run the command `go mod init learn-gin` This will initialize a new Go module.

We also need to install Gin Web Framework, use the below command to get it from GitHub.

```bash
$ go get -u github.com/gin-gonic/gin
```

# Code

## main.go

```go
package main

import (
	"log"

	"learn-gin/web"
)

func main() {
	r := web.Router()
	log.Fatal(r.Run())
}
```

* This is the entry point of the application.
    
* It imports the `web` package, which contains the routing logic.
    
* In the `main` function, it initializes a router using the `web.Router()` function.
    
* The [`r.Run`](http://r.Run)`()` function starts the HTTP server and begins listening for incoming requests.
    
* If an error occurs while starting the server, the application will log the error using `log.Fatal()`.
    

## web/assignments.go

```go
package web

import (
	"github.com/gin-gonic/gin"
)

type Assignments struct{}

func (a *Assignments) Index(c *gin.Context) {
	c.JSON(200, gin.H{
		"assignments": []string{},
	})
}
```

* This file defines a struct named `Assignments`.
    
* The `Assignments` struct does not have any fields, but it has a method named `Index` associated with it.
    
* The `Index` method is a route handler function that accepts a Gin context (`c *gin.Context`) as a parameter.
    
* When an HTTP GET request is made to the `/assignments` endpoint, the `Index` function responds with a JSON object containing an empty array under the "assignments" key.
    

## web/router.go

```go
package web

import (
	"github.com/gin-gonic/gin"
)

func Router() *gin.Engine {
	r := gin.Default()
	asgns := Assignments{}
	r.GET("/assignments", asgns.Index)
	return r
}
```

* This file defines a function named `Router` that creates and configures a Gin router.
    
* Inside the `Router` function, a new Gin router is created using `gin.Default()`. This sets up a basic router with default middleware, including logging and recovery.
    
* An instance of the `Assignments` struct is created.
    
* The `/assignments` endpoint is associated with the `Index` method of the `Assignments` struct, so when a GET request is made to this endpoint, the `Index` function is called to handle the request.
    
* The function returns the configured router.
    

When you run the application, it starts an HTTP server that listens on a port (default is 8080), and when you access the `/assignments` endpoint, it responds with a JSON object containing an empty array.

# Thanks for reading

If you're interested in delving deeper into topics like DSA, Blockchain, and Backend, make sure to follow me on Twitter ([@jyotirmoydotdev](https://twitter.com/jyotirmoydotdev)) and subscribe to my [newsletter](https://jyotirmoy.hashnode.dev/newsletter) for the latest blog posts.