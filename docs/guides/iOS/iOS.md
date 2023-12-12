---
currentMenu: ios-Installation
---

## 📝 Requirements

* iOS 11.0+ / tvOS 12.0+ / macOS 10.15+ / watchOS 6.0+
* Swift 5.0+

## 📦 Installation

### SPM
~~~
.package(url: "https://github.com/nstack-io/nstack-ios-sdk", from: "5.0.0"),
~~~

To use localizations in a separate module, you probably want to do something like this:
~~~
.target(
    name: "Localizations",
    dependencies: [
        .product(name: "NStackSDK",
                 package: "nstack-ios-sdk"),
    ],
    exclude: ["nstack-localizations-generator.bundle"],
    resources: [
        .copy("NStack.plist"),
        .copy("Localizations/Localizations_en-GB.json"),
        .copy("Localizations/Localizations_de-DE.json")
    ]
)
~~~

### CocoaPods
~~~
pod 'NStackSDK', '~> 5.2.0'
~~~


## 💻 Usage

> **NOTE:** Don't forget to `import NStackSDK` in the top of the file.

### Getting Started

#### Plist

In your AppDelegate's `didFinishLaunching:` function start NStack by running:

~~~swift
let configuration = NStackSDK.Configuration(plistName: "Nstack",
                                            environment: .production,
                                            localizationClass: Localizations.self)

NStack.start(configuration: configuration, launchOptions: nil)
~~~

You should have a file called NStack.plist in your application bundle. It needs to contain a key called **`REST_API_KEY`** and a key called **`APPLICATION_ID`**.



You can also use an alternative initializer for the `NStackSDK.Configuration` and just pass the **`REST_API_KEY`** and **`APPLICATION_ID`** directly. 


