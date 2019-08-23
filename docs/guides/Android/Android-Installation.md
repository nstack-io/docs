---
currentMenu: android-Installation
---

## 📦 Installation

1. Open `build.gradle` file located in your project folder
2. Add the NStack SDK dependency and sync your project
```groovy
dependencies {
    implementation "dk.nodes.nstack:nstack-kotlin:3.0.5"
}
```
3. After synchronisation is complete, you can start using the NStack SDK

## Dependencies
- okhttp 3.8.0



## ⚒ Configuration
 In order to use the NStack SDK you have to initilize and configure it first.

In order to connect the NStack API with your application you will need `ApplicationId`, `REST API Key`. 

For more information how to get these keys checkout our  [Getting Start Guide](https://nstack-io.github.io/documentation/docs/guides/getting-started.html).

Put the `ApplicationId`, `REST API Key` keys as meta-data in your `AndroidManifest.xml` like so:
```xml
<application>
       <meta-data
           android:name="dk.nodes.nstack.appId"
           android:value="your application Id"
           tools:replace="android:value" />


       <meta-data
           android:name="dk.nodes.nstack.apiKey"
           android:value="your REST API key"
           tools:replace="android:value" />

       <meta-data
          android:name="dk.nodes.nstack.env"
          android:value="staging"
          tools:replace="android:value" />

          ....

</application/>
```

> You can also put these values into your `build.gradle` and use placeholders in the manifest

 Best place to initialise the SDK will be in you Application's `onCreate()` method as it requires your application's `Context`. 

 `Application` is the class for maintaining global application state. 

 Here is a basic SDK initialisation example:

```kotlin
class MyApplication : Application() {
   override fun onCreate(){
     super.onCreate()
     // Specify your Translation class where translation string will be stored
     NStack.translationClass = Translation::class.java
     // initilize the SDK
     NStack.init(this)

   }
}
```
There also **optional** parameters you could make use of while using NStack SDK:

```kotlin
NStack.debugMode = true - Enables debug mode for the library (Outputs messages to log)
NStack.setRefreshPeriod(60, TimeUnit.MINUTES) - Allows you to set the period for how often NStack should check for updates
```
> Warning: In almost every instance you want to set these optional methods before NStack is initialized