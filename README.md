<div align="center"><img src="al.png" /></div>

**SuperCereal** is a simple and efficient JSON serialization library for Go. Unlike most other serializers, including Go's `json.Marshal` and JavaScript's `JSON.stringify`, it doesn't operate using an intermediary tree data structure. This makes it significantly more efficient in both time and memory. Because it doesn't use third-party non-standard preprocessing, your code remains purely standard & portable Golang.

## 17x the json.Marshal performance
```go
var json []byte = supercereal.Marshal(func(object *supercereal.JSONObject) {
  object.Put("firstName", "John")
  object.Put("lastName", "Smith")
  object.Put("isAlive", true)
  object.Put("age", 25)
  object.Put("address", func(object *supercereal.JSONObject) {
    object.Put("streetAddress", "21 2nd Street")
    object.Put("city", "New York")
    object.Put("state", "NY")
    object.Put("postalCode", "10021-3100")
  })
  object.Put("phoneNumbers", func(array *supercereal.JSONArray) {
    array.Put(func(object *supercereal.JSONObject) {
      object.Put("type", "home")
      object.Put("number", "212 555-1234")
    })
    array.Put(func(object *supercereal.JSONObject) {
      object.Put("type", "office")
      object.Put("number", "646 555-4567")
    })
    array.Put(func(object *supercereal.JSONObject) {
      object.Put("type", "mobile")
      object.Put("number", "123 456-7890")
    })
  })
  object.Put("children", func(array *supercereal.JSONArray) {})
  object.Put("spouse", nil)
})
```

*Licensed Zlib © 2017 - 2019*
