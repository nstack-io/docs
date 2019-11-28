---
currentMenu: ios-Responses
---

## Responses on iOS

Responses allow you to define and update JSON files on the NStack web console and retrieve them using the NStack sdk or using a normal get request.

Read more in the [*Features/Responses*](../../features/responses.html) section on what you can do with Responses.

~~~~swift
NStack.sharedInstance.getContentResponse(id) { (data, error) in
  guard error == nil else {
    print("Error fetching response with id: \(id)")
    return
  }
            
  // Use data
}
~~~~

Version 4.0.x changed the way to get a Response from the NStack:
~~~~swift
NStack.sharedInstance.contentManager?.getContentResponse("name of slug", completion: { (result: Result<T, Error>>) -> Void in
        switch result {
        case .success(let response):
            completion(.success(response))
        case .failure(let error):
            completion(.failure(error))
        }
    })
~~~~


