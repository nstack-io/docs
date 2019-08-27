---
currentMenu: ios-Files
---

## Files on iOS
With files you can retrieve files defined on the NStack web console using a normal get request.
The files functionality has not been implemented in the sdk.

Read a more detailed explanation about **Files** in [*Features/Files*](../../features/files.html)

~~~~swift
if let url = URL(string: url) {
  URLSession.shared.downloadTask(with: url) { (localURL, urlResponse, error) in
    guard error == nil else {
        print("Error fetching file with url: \(url)")
        print(error)
        return
    }

    if let localURL = localURL {
        print("Local URL: \(localURL)")
        // Use the localURL to modify, use your newly downloaded file
    }
  }.resume()
}
~~~~