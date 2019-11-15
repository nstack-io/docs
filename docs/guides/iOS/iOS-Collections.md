---
currentMenu: ios-Collections
---

## Collections on iOS
Collections is a more structured version of Responses and can be used as an alternative to an simple read API.

Read a more detailed explanation about **Collections** in [*Features/Collections*](../../features/collections.html)

~~~~swift
let completion: (NStack.Result<Product>) -> Void = { result in
  switch result {
  case .success(let data):
    print("Fetching collection successful")
    print(data)
  case .failure(let error):
    print("Error fetching collection: \(error)")
  }
}
        
NStack.sharedInstance.fetchCollectionResponse(for: id, completion: completion)
~~~~

Version 4.0.x changed the way to get a Response from the NStack:
~~~~swift
NStack.sharedInstance.contentManager?.fetchCollectionResponse(for: "id of slug as Int", completion: { (result: <Result<T, Error>>) in
				switch result {
        case .success(let response):
            completion(.success(response))
        case .failure(let error):
            completion(.failure(error))
        }
    })
~~~~