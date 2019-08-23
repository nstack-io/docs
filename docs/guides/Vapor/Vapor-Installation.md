---
currentMenu: Vapor-Installation
---

## 📦 Installation

### Package.swift

Add `NStack` to the Package dependencies:

```swift
dependencies: [
    // ...,
    .package(url: "https://github.com/nodes-vapor/nstack.git", .from(from: "3.0.0-beta"))
]
```

as well as to your target (e.g. "App"):

```swift
targets: [
    .target(name: "App", dependencies: [..., "NStack", ...]),
    // ...
]
```

## Getting started 🚀

Import NStack where needed:
```swift
import NStack
```

### Config

Create `NStack.Config` to configure `NStack`, your `Applications` as well as the default `Translate.Config`.

```swift
let nstackConfig = NStack.Config(
    applicationConfigs: [
        Application.Config(
            name: "my app name",
            applicationId: "NEVER_PUT_API_IDS_IN_SOURCE_CODE",
            restKey: "NEVER_PUT_API_KEYS_IN_SOURCE_CODE"
        )
    ],
    defaultTranslateConfig: TranslateController.Config(
        defaultPlatform: .backend,
        defaultLanguage: "en-EN",
        cacheInMinutes: 1
    ),
    log: false
)
```

If you set `log` to `true` you will receive helpful logs in case anything goes wrong.


### Adding the Service

Instantiate and register `NStackProvider` with config created in the previous step.
If you plan on using the leaf tag (see below), make sure to use a synchronous cache, such as `MemoryKeyedCache` (and not `RedisCache`); otherwise it might break your leaf templates, see https://github.com/vapor/leaf/issues/134

In `configure.swift`:
```swift
// MARK: NStack
try services.register(
    NStackProvider(
        config: nstackConfig,
        cacheFactory: { container in try container.make(MemoryKeyedCache.self) }
    )
)
```