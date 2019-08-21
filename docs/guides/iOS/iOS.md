## 📝 Requirements

* iOS 8.0+ / tvOS 9.0+ / macOS 10.10+ / watchOS 2.0+
* Swift 3.0+

## 📦 Installation

### Carthage
~~~
# Swift 5
github "nodes-ios/NStackSDK" ~> 3.0

# Swift 4.2-5 using Alamofire 5 - Pre-release
github "nodes-ios/NStackSDK" "feature/alamofire5"

# Swift 3-4
github "nodes-ios/NStackSDK" ~> 2.0

# Swift 2.3
github "nodes-ios/NStackSDK" == 0.3.12

# Swift 2.2
github "nodes-ios/NStackSDK" == 0.3.10
~~~
### Migration Swift 4.x -> Swift 5

1. Put this line in the cartfile
~~~
 github "nodes-ios/NStackSDK" ~> 3.0
~~~
2. Remove all other references to Alamofire and Serpent from the Cartfile
3. run ```carthage update NStackSDK``` for your platform

### Migration to NStackSDK with Alamofire 5
1. Put this line in the Cartfile
~~~
github "nodes-ios/NStackSDK" "feature/alamofire5"
~~~
2. Remove all other references to Alamofire and Serpent from the Cartfile
3. Make sure you don't have other dependencies using Alamofire 4 or Serpent ~> 1.0. If you have, refer to the github repo for the dependency for migration pointers
3. run ```carthage update NStackSDK``` for your platform

## 💻 Usage

> **NOTE:** Don't forget to `import NStackSDK` in the top of the file.

### Getting Started

#### Plist

In your AppDelegate's `didFinishLaunching:` function start NStack by running:

~~~swift
let configuration = Configuration(plistName: "NStack", translationsClass: Translations.self)
NStack.start(configuration: configuration, launchOptions: launchOptions)
~~~

You should have a file called NStack.plist in your application bundle. It needs to contain a key called **`REST_API_KEY`** and a key called **`APPLICATION_ID`**.

=======================

