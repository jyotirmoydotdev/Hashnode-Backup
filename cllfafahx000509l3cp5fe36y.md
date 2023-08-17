---
title: "A simple HTTP server using Golang"
datePublished: Thu Aug 17 2023 14:59:37 GMT+0000 (Coordinated Universal Time)
cuid: cllfafahx000509l3cp5fe36y
slug: a-simple-http-server-using-golang
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692284212452/26b376ab-2d1a-4492-8b92-cdfbc77fe811.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692285232939/b9cf9401-6885-4e66-8472-0c667de8a7f0.jpeg
tags: server, golang

---

# Print "Hello World"

We are going to see how to create a simple HTTP server that listens on port 6688. When a request is made to the `/helloworld` path, the `helloworld()` function is called. This function simply prints "Hello World" to the response writer.

Create a file `main.go`

```go
package main

import (
	"fmt"
	"log"
	"net/http"
)
func helloworld(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "Hello World")
}

func main() {
	http.HandleFunc("/helloworld", helloworld)
	log.Fatal(http.ListenAndServe(":6688", nil))
}
```

Here is a more detailed explanation of the code:

* The `package main` statement tells the Go compiler that this code is in the `main` package.
    
* The `import` statements import the `fmt`, `log`, and `net/http` packages.
    
* The `func helloworld(w http.ResponseWriter, r *http.Request)` function is a simple function that prints "Hello World" to the response writer.
    
* The `func main()` function is the entry point for the program. It calls the `http.HandleFunc()` method to tell the HTTP server to handle requests for the `/helloworld` path with the `helloworld()` function. It then calls the `http.ListenAndServe()` method to start the HTTP server.
    

To run the code, you can save it in a file called main.go and then run the following command:

```go
$ go run main.go
```

This will start the HTTP server and you can then access it by opening a web browser and navigating to [http://localhost:6688/helloworld](http://localhost:6688/helloworld).

# Return JSON

We have seen how to print "Hello world" Now we are going to see how to create a server that when a request is made to the `/getbook` path, the `GetBook()` function is called. This function returns a JSON representation of a book object.

Create `main1.go`

```go
package main

import (
	"encoding/json"
	"log"
	"net/http"
)

type Book struct {
	Title  string `json:"title"`
	Author string `json:"author"`
	Pages  int    `json:"pages"`
}

func GetBook(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "application/json")
	book := Book{
		Title:  "Golang Book",
		Author: "Google",
		Pages:  300,
	}
	json.NewEncoder(w).Encode(book)
}

func main() {
	http.HandleFunc("/getbook", GetBook)
	log.Fatal(http.ListenAndServe(":6688", nil))
}
```

Here is a more detailed explanation of the code:

* The `package main` statement tells the Go compiler that this code is in the `main` package.
    
* The `import` statements import the `encoding/json`, `log`, and `net/http` packages.
    
* The `type Book struct` statement defines a struct called `Book`. This struct has three fields: `Title`, `Author`, and `Pages`.
    
* The `func GetBook(w http.ResponseWriter, r *http.Request)` function is the function that is called when a request is made to the `/getbook` path. This function sets the `Content-Type` header to `application/json` and then encodes a `Book` object into JSON and writes it to the response writer.
    
* The `func main()` function is the entry point for the program. It calls the `http.HandleFunc()` method to tell the HTTP server to handle requests for the `/getbook` path with the `GetBook()` function. It then calls the `http.ListenAndServe()`method to start the HTTP server.
    

To run the code, you can save it in a file called main1.go and then run the following command:

```go
$ go run main1.go
```

This will start the HTTP server and you can then access it by opening a web browser and navigating to [http://localhost:6688/getbook](http://localhost:6688/getbook)

# Thanks for reading

I appreciate you taking the time to read this. If you found it helpful, please subscribe to my newsletter and give it a like.