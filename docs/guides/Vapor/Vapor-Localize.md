## Localize on Vapor

Read more about **Localization** in the [*Feature/Localization*](../../features/localize.html) section.

```swift
func getProductName(req: Request) throws -> Future<String> {

    // ...

    let nstack = try req.make(NStack.self)
    let translation = nstack.application.translate.get(on: req, section: "products", key: "nstackForSale")

    return translation
}
```

You can also provide `searchReplacePairs`:

```swift
func getProductName(req: Request, owner: String) throws -> Future<String> {

    let nstack = try req.make(NStack.self)
    let translation = nstack.application.translate.get(
        on: req,
        section: "products",
        key: "nstackForSale",
        searchReplacePairs: [
            "productOwner" : owner
        ]
    )

    return translation
}
```

If you are using multiple NStack applications within your project you can switch them with `getApplication()`:

```swift
let nstack = try req.make(NStack.self)
let translation = nstack.getApplication("my app name").translate.get(on: req, section: "products", key: "nstackForSale")
```

Note: you can specify the `get()` call further in case you don't want to go with the values provided in `defaultTranslateConfig`:

```swift
let translation = nstack.application.translate.get(
    on: req,
    platform: .backend,
    language: "dk-DK",
    section: "products",
    key: "nstackForSale",
    searchReplacePairs: [
        "productOwner" : "Christian"
    ]
)
```

### Leaf Tag

In order to render the NStack Leaf tags, you will need to add them first:

```swift
public func configure(_ config: inout Config, _ env: inout Environment, _ services: inout Services) throws {
    services.register { container -> LeafTagConfig in
        var tags = LeafTagConfig.default()
        try tags.useNStackLeafTags(container)
        return tags
    }
}
```

NStack comes with a built-in Leaf tag. The tag yields a translated string or the given key if translation fails

```swift
// Get translation for camelCasedSection.camelCasedKey
#nstack:translate("camelCasedSection", "camelCasedKey")

// Get translation for camelCasedSection.camelCasedKey and replace searchString1 with replaceString1 etc
#nstack:translate("camelCasedSection", "camelCasedKey", "searchString1", "replaceString1", "searchString2", "replaceString2", ...)
```

*IMPORTANT:* Due to a bug in leaf you have to make sure that the translations are already loaded and available synchronously when rendering the view. This can be achieved by using the `NStackPreloadMiddleware` on the routes for your views:

```swift
let nstackPreloadMiddleware = try container.make(NStackPreloadMiddleware.self)
let unprotectedBackend = router.grouped(nstackPreloadMiddleware)

```

Please note that the leaf tag always uses the **current application** with the **default translate config** that you have provided.