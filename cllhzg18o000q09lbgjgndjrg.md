---
title: "Building a JSON Validation Pipeline with Go and Gin"
datePublished: Sat Aug 19 2023 12:15:34 GMT+0000 (Coordinated Universal Time)
cuid: cllhzg18o000q09lbgjgndjrg
slug: building-a-json-validation-pipeline-with-go-and-gin
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692447263482/0cc5195e-cbd7-45b9-866c-53f90134e494.jpeg
tags: golang

---

# Introduction

Imagine a scenario where we're transmitting crucial data from our website to a database. However, before this information is stored, we need to ensure that the incoming JSON is in the correct format with all the required fields. This task of validating JSON becomes pivotal to maintaining data integrity. Thankfully, a straightforward solution comes in the form of creating a web service using Go and harnessing the power of the Gin web framework.

In this article, we will construct a pipeline to validate JSON data against predefined structures. For example, suppose we require JSON data of a book from a website, something like this:

```json
{
  "title": "The Catcher in the Rye",
  "author": "J.D. Salinger",
  "publication_year": 1951,
  "isbn": "978-0-316-76949-3",
  "genre": "Fiction",
  "language": "English",
  "publisher": "Little, Brown and Company",
  "page_count": 224,
  "summary": "A novel about a teenager's experiences in New York City...",
  "cover_image_url": "https://example.com/book/catcher-in-the-rye-cover.jpg",
  "ratings": {
    "average": 4.2,
    "count": 1205
  },
  "reviews": [
    {
      "user": "reader123",
      "rating": 5,
      "review_text": "A classic coming-of-age story."
    },
    {
      "user": "booklover456",
      "rating": 4,
      "review_text": "Well-written and thought-provoking."
    }
  ]
}
```

# Full Code

So, this code defines a basic web service that validates incoming JSON data against a predefined `Book` struct using reflection and the Gin framework. It ensures that the received JSON adheres to the expected structure of a book's details.

```go
package main

import (
	"encoding/json"
	"fmt"
	"log"
	"net/http"
	"reflect"

	"github.com/gin-gonic/gin"
)

type Book struct {
	Title            string    `json:"title"`
	Author           string    `json:"author"`
	Publication_Year int       `json:"publication_year"`
	ISBN             string    `json:"isbn"`
	Genre            string    `json:"genre"`
	Language         string    `json:"language"`
	Publisher        string    `json:"publisher"`
	Page_Count       int       `json:"page_count"`
	Summary          string    `json:"summary"`
	Cover_Image_URL  string    `json:"cover_image_url"`
	Ratings          ratings   `json:"ratings"`
	Reviews          []reviews `json:"reviews"`
}
type ratings struct {
	Average float64 `json:"average"`
	Count   int     `json:"count"`
}
type reviews struct {
	User        string `json:"user"`
	Rating      int    `json:"rating"`
	Review_Text string `json:"review_text"`
}

func main() {
	r := Router()
	log.Fatal(r.Run())
}
func Router() *gin.Engine {
	router := gin.Default()
	router.POST("/validate-book", ValidateBook)
	return router
}
func ValidateBook(c *gin.Context) {
	var receivedData map[string]interface{}
	if err := json.NewDecoder(c.Request.Body).Decode(&receivedData); err != nil {
		c.JSON(http.StatusBadRequest, gin.H{
			"error": "Invalid JSON",
		})
		return
	}

	if len(receivedData) == 0 {
		c.JSON(http.StatusBadRequest, gin.H{
			"error": "Empty JSON",
		})
		return
	}

	bookType := reflect.TypeOf(Book{})
	validFields := make(map[string]bool)

	for i := 0; i < bookType.NumField(); i++ {
		field := bookType.Field(i)
		validFields[field.Tag.Get("json")] = true
	}

	for key := range receivedData {
		if !validFields[key] {
			c.JSON(http.StatusBadRequest, gin.H{
				"error": fmt.Sprintf("Invalid field: %s", key),
			})
			return
		}
	}

	c.JSON(http.StatusOK, gin.H{
		"message": "JSON structure matches Book struct",
	})
}
```

# Import Statements

The code starts by importing various packages that are necessary for its functionality. These packages include:

* `encoding/json`: This package provides functions for encoding and decoding JSON data.
    
* `fmt`: It's used for formatted I/O operations like printing to the console.
    
* `log`: This package allows for logging error messages.
    
* `net/http`: It provides HTTP client and server implementations.
    
* `reflect`: This package provides runtime type introspection, which allows you to examine the structure of types at runtime.
    
* [`github.com/gin-gonic/gin`](http://github.com/gin-gonic/gin): This is the Gin web framework, which simplifies building web applications in Go.
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">To install <strong>Gin</strong>, run the command <code>go get github.com/gin-gonic/gin</code></div>
</div>

```go
package main

import (
	"encoding/json"
	"fmt"
	"log"
	"net/http"
	"reflect"

	"github.com/gin-gonic/gin"
)
```

# Data Structures

`Book` is a struct that represents the details of a book. Each field in the struct corresponds to a specific attribute of a book (e.g., title, author, etc.). The `json` tags associated with each field define how the field should be encoded/decoded in JSON.

`ratings` and `reviews` are the nested structs that store information about the book's ratings and reviews, respectively.

```go
type Book struct {
	Title            string    `json:"title"`
	Author           string    `json:"author"`
	Publication_Year int       `json:"publication_year"`
	ISBN             string    `json:"isbn"`
	Genre            string    `json:"genre"`
	Language         string    `json:"language"`
	Publisher        string    `json:"publisher"`
	Page_Count       int       `json:"page_count"`
	Summary          string    `json:"summary"`
	Cover_Image_URL  string    `json:"cover_image_url"`
	Ratings          ratings   `json:"ratings"`
	Reviews          []reviews `json:"reviews"`
}
type ratings struct {
	Average float64 `json:"average"`
	Count   int     `json:"count"`
}
type reviews struct {
	User        string `json:"user"`
	Rating      int    `json:"rating"`
	Review_Text string `json:"review_text"`
}
```

# Main Function `main()`

In the main function, we will just initialize a Gin router using the `Router()` function and then starts the server to listen for incoming requests.

```go
func main() {
	r := Router()
	log.Fatal(r.Run())
}
```

# Router Function `Router()`

Now creates a new instance of the Gin router and configure it with default settings. It registers a single route that points to the `ValidateBook` handler function.

```go
func Router() *gin.Engine {
	router := gin.Default()
	router.POST("/validate-book", ValidateBook)
	return router
}
```

# **ValidateBook Handler Function**

This function is responsible for validating incoming JSON data against the predefined `Book` struct.

It begins by attempting to decode the JSON data received in the request's body. If the decoding fails (e.g., due to malformed JSON), it responds with an error indicating invalid JSON.

If the JSON data is empty, it responds with an error indicating an empty JSON object.

```go
func ValidateBook(c *gin.Context) {
	var receivedData map[string]interface{}
	if err := json.NewDecoder(c.Request.Body).Decode(&receivedData); err != nil {
		c.JSON(http.StatusBadRequest, gin.H{
			"error": "Invalid JSON",
		})
		return
	}
    if len(receivedData) == 0 {
		c.JSON(http.StatusBadRequest, gin.H{
			"error": "Empty JSON",
		})
		return
	}
}
```

# Reflection and Validation

The code employs reflection to dynamically inspect the fields of the `Book` struct and their associated JSON tags.

It iterates through the fields of the `Book` struct and populates a `validFields` map with the JSON tag names. This map will be used to validate the received JSON keys.

Subsequently, the code iterates through the keys in the received JSON data and checks if they match any valid fields. If a key doesn't correspond to any valid field, it responds with an error indicating an invalid field.

```go
func ValidateBook(c *gin.Context) {
	var receivedData map[string]interface{}
	if err := json.NewDecoder(c.Request.Body).Decode(&receivedData); err != nil {
		c.JSON(http.StatusBadRequest, gin.H{
			"error": "Invalid JSON",
		})
		return
	}

	if len(receivedData) == 0 {
		c.JSON(http.StatusBadRequest, gin.H{
			"error": "Empty JSON",
		})
		return
	}

	bookType := reflect.TypeOf(Book{})
	validFields := make(map[string]bool)

	for i := 0; i < bookType.NumField(); i++ {
		field := bookType.Field(i)
		validFields[field.Tag.Get("json")] = true
	}

	for key := range receivedData {
		if !validFields[key] {
			c.JSON(http.StatusBadRequest, gin.H{
				"error": fmt.Sprintf("Invalid field: %s", key),
			})
			return
		}
	}

	c.JSON(http.StatusOK, gin.H{
		"message": "JSON structure matches Book struct",
	})
}
```

# Response

If the received JSON data structure matches the fields and JSON tags of the `Book` struct, the handler responds with an HTTP status indicating success, along with a message stating that the JSON structure matches the `Book` struct.

```bash
{"message": "JSON structure matches Book struct"}
```

# Test Using Thunder Client

Start the server using the command `go run main.go`

If you are utilizing Thunder clint, you can take advantage of the "Body/JSON" section to facilitate testing. This feature allows you to simulate sending JSON payloads to the server, helping you validate the behavior of your web service's JSON validation pipeline. By employing the "Body/JSON" testing capability, you can efficiently assess how your server responds to various JSON structures and ensure that the validation mechanism operates as intended.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692444765098/0fd96de4-8c65-492d-b41e-a82152cbba06.png align="center")

# Test With CURL

Start the server using the command `go run main.go`

To further validate the effectiveness of your JSON validation pipeline, you can perform testing using the powerful command-line tool, `curl`. With `curl`, you can simulate HTTP requests directly from your terminal and observe how your server responds to different scenarios. Here's how you can use `curl` to conduct tests on your Go and Gin-based JSON validation server:

### **Sending Valid JSON:**

To simulate sending valid JSON data to your server, use the following command:

```bash
curl -X POST -H "Content-Type: application/json" -d "{\"title\": \"The Catcher in the Rye\",\"author\": \"J.D. Salinger\",\"publication_year\": 1951,\"isbn\": \"978-0-316-76949-3\",\"genre\": \"Fiction\",\"language\": \"English\",\"publisher\": \"Little, Brown and Company\",\"page_count\": 224,\"summary\": \"A novel about a teenager's experiences in New York City...\",\"cover_image_url\": \"https://example.com/book/catcher-in-the-rye-cover.jpg\",\"ratings\": {\"average\": 4.2,\"count\": 1205},\"reviews\": [{\"user\": \"reader123\",\"rating\": 5,\"review_text\": \"A classic coming-of-age story.\"},{\"user\": \"booklover456\",\"rating\": 4,\"review_text\": \"Well-written and thought-provoking.\"}]}" http://0.0.0.0:8080/validate-book
```

**Output**

```bash
{"message":"JSON structure matches Book struct"}% 
```

By issuing this command, you're sending a POST request with properly formatted JSON containing all the required fields. Observe the server's response to confirm that the JSON validation pipeline is functioning as intended.