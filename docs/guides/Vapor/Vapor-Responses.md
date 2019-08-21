## Responses on Vapor

NStack can be used to store JSON responses. To make use of this feature you can use the `ResponseController`.

```swift
let nstack = try NStack.makeService(for: req)
nstack.application.response[42].do { (response: Response) in
	print(response.content)
}
```

This gets the unmodified NStack `Response` with your JSON data in an object keyed by `data`, eg.:

```
{"data":{"myJSONData":"Starts here"}}
```

Alternatively you can decode your JSON object like so:

```swift
nstack.application.response[42].do { (response: [String: String]) in
	print(response)
}
```

This would yield your `Decodable` object, in this case our dictionary: `["myJSONData": "Starts here"]`.

Read more in the [*Features/Responses*](../../features/responses.html) section on what you can do with Responses.
