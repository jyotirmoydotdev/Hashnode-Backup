---
title: "Time Based Key-Value Store - Leetcode 981"
datePublished: Wed Jan 03 2024 15:25:18 GMT+0000 (Coordinated Universal Time)
cuid: clqxxjqco00000alba1tb6s4k
slug: leetcode-0981
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704295456514/7b784070-6193-439d-ba62-082d6d5a999a.jpeg
tags: go, leetcode

---

# Problem - [Leetcode](https://leetcode.com/problems/time-based-key-value-store/description/)

Design a time-based key-value data structure that can store multiple values for the same key at different time stamps and retrieve the key's value at a certain timestamp.

Implement the `TimeMap` class:

* `TimeMap()` Initializes the object of the data structure.
    
* `void set(String key, String value, int timestamp)` Stores the key `key` with the value `value` at the given time `timestamp`.
    
* `String get(String key, int timestamp)` Returns a value such that `set` was called previously, with `timestamp_prev <= timestamp`. If there are multiple such values, it returns the value associated with the largest `timestamp_prev`. If there are no values, it returns `""`.
    

**Example 1:**

```go
Input
["TimeMap", "set", "get", "get", "set", "get", "get"]
[[], ["foo", "bar", 1], ["foo", 1], ["foo", 3], ["foo", "bar2", 4], ["foo", 4], ["foo", 5]]
Output
[null, null, "bar", "bar", null, "bar2", "bar2"]

Explanation
TimeMap timeMap = new TimeMap();
timeMap.set("foo", "bar", 1);  // store the key "foo" and value "bar" along with timestamp = 1.
timeMap.get("foo", 1);         // return "bar"
timeMap.get("foo", 3);         // return "bar", since there is no value corresponding to foo at timestamp 3 and timestamp 2, then the only value is at timestamp 1 is "bar".
timeMap.set("foo", "bar2", 4); // store the key "foo" and value "bar2" along with timestamp = 4.
timeMap.get("foo", 4);         // return "bar2"
timeMap.get("foo", 5);         // return "bar2"
```

 **Constraints:**

* `1 <= key.length, value.length <= 100`
    
* `key` and `value` consist of lowercase English letters and digits.
    
* `1 <= timestamp <= 10<sup>7</sup>`
    
* All the timestamps `timestamp` of `set` are strictly increasing.
    
* At most `2 * 10<sup>5</sup>` calls will be made to `set` and `get`.
    

# Solution in Golang

```go
type TimeMap struct {
	store map[string][]ValStamp
}

type ValStamp struct {
	Val  string
	Time int
}

func Constructor() TimeMap {
	return TimeMap{store: make(map[string][]ValStamp)}
}

func (this *TimeMap) Set(key string, value string, timestamp int) {
	if _, ok := this.store[key]; !ok {
		this.store[key] = make([]ValStamp, 0)
	}
	this.store[key] = append(this.store[key], ValStamp{value, timestamp})
}

func (this *TimeMap) Get(key string, timestamp int) string {
	var res string
	var values []ValStamp
	if _, ok := this.store[key]; ok {
		values = this.store[key]
	}
	l, r := 0, len(values)-1
	for l <= r {
		mid := l + (r-l)/2
		if values[mid].Time <= timestamp {
			res = values[mid].Val
			l = mid + 1
		} else {
			r = mid - 1
		}
	}
	return res
}
```

This code defines a `TimeMap` struct, which is essentially a key-value store where each key can have multiple values associated with different timestamps. Here's a detailed breakdown:

1. **TimeMap Struct:**
    
    * `TimeMap` is defined with a single field, `store`, which is a map with string keys and slices of `ValStamp` values.
        
    * `ValStamp` is a struct representing a value and its associated timestamp.
        
2. **Constructor:**
    
    * The `Constructor` function initializes and returns a new `TimeMap` with an empty map as its store.
        
3. **Set Method:**
    
    * `Set` adds a new value along with its timestamp to the map for a given key.
        
    * If the key doesn't exist in the map, it initializes an empty slice for that key.
        
    * It then appends a new `ValStamp` to the slice with the provided value and timestamp.
        
4. **Get Method:**
    
    * `Get` retrieves the value associated with a key at or before the specified timestamp.
        
    * It initializes two pointers, `l` (left) and `r` (right), for a binary search within the stored values.
        
    * The function iteratively performs a binary search to find the closest timestamp that is less than or equal to the given timestamp.
        
    * The result is updated as it searches, and the final result is the value associated with the found timestamp.
        

In summary, this code implements a time-based key-value store where values are associated with timestamps, and the `Get` method retrieves the value closest to or at a specified timestamp using binary search on the stored timestamps.