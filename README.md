# Better Cache ![Stars](https://img.shields.io/github/stars/realTristan/BetterCache?color=brightgreen) ![Watchers](https://img.shields.io/github/watchers/realTristan/BetterCache?label=Watchers)
![banner (5)](https://user-images.githubusercontent.com/75189508/186757681-6b7f97e8-ec37-448a-83cc-75106ed16309.png)

Lightning Fast Caching System for Go.

# About
- Better Cache is an ultra fast caching system that uses an array of bytes for storing data instead of the very common map caching system. Because the data is stored in an array of bytes instead of a map, it enables lightning fast full text searches. (within microseconds to milliseconds)
- Better Cache also uses solely native golang modules which makes it fast, lightweight and secure.

# Benchmarks

<h3>Full Text Search</h3>

```
    (1) Cache Size: 25 -> ~32µs
    (10) Cache Size: 250 -> ~62µs
    (100) Cache Size: 2,500 -> ~172µs
    (1,000) Cache Size: 25,000 -> ~1.33ms
    (10,000) Cache Size: 250,000 -> ~13.87ms
```

# Quick Usage

```go
package main

import (
    "fmt"
    "github.com/realTristan/BetterCache"
)

func main() {
    // Add key1 to the cache
    cache.Set("key1", map[string]string{
		"summary": "My name is \"Tristan\"",
	})

    // Get key from the cache
    var data = cache.Get("key1")
    fmt.Println(data)

    // Full Text Search for the key's contents
	var res = cache.FullTextSearch(cache.TextSearch{
		Limit:      -1,                 // No limit
		Query:      []byte("tristan"),  // Search for "tristan"
		StrictMode: false,              // Ignore CAPS
	})
    fmt.Println(res)

    // Remove key1 from the cache
    cache.Remove("key1")
}

```

# License
MIT License

Copyright (c) 2022 Tristan Simpson

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
