---
currentMenu: android-Installation
---

## 📦 Installation  

1\. Open the `build.gradle` file of the module you plan to use NStack in

2\. Add the NStack SDK dependency and sync your project

``` groovy
dependencies {
    ...
    
    implementation "dk.nodes.nstack:nstack-kotlin:<LATEST_VERSION>"
}
```

3\. Add the translation plugin to your root project's `build.gradle` file:

``` groovy
dependencies { 
    ...
    
    classpath "dk.nodes.nstack:translation:<LATEST_VERSION>"
}
```

Replace `<LATEST_VERSION>` in both places with the latest library version. You can find the latest version in the badge below (remove the `v` when adding the version to your gradle files).

<br />
![NStack Badge](https://img.shields.io/maven-central/v/dk.nodes.nstack/nstack-kotlin.svg)  

<br />
4\. After the synchronisation is complete, you can start configuring the NStack SDK

## Dependencies

* okhttp 3.8.0

## ⚒ Configuration

In order to use the NStack SDK, you have to initilize and configure it first. The NStack API requires an application ID and an API key. For more information on how to obtain these, please read our [Getting Started Guide](https://nstack-io.github.io/documentation/docs/guides/getting-started.html).

Once you have the keys, put them in your `AndroidManifest.xml` together with the environment name. Since it is highly likely you will have multiple environment names based on your build type or variant, you might want to set the environment name for each using [manifest placeholders](https://developer.android.com/studio/build/manifest-build-variables) rather than directly.

``` xml
<application ...>
       
        <meta-data
            android:name="dk.nodes.nstack.appId"
            android:value="<YOUR APPLICATION ID>"
            tools:replace="android:value" />

        <meta-data
            android:name="dk.nodes.nstack.apiKey"
            android:value="<YOUR REST API KEY>"
            tools:replace="android:value" />

        <meta-data
            android:name="dk.nodes.nstack.env"
            android:value="<YOUR ENVIRONMENT NAME>"
            tools:replace="android:value" />

        ...

</application/>
```

 We recommend initializing the SDK inside your [application](https://developer.android.com/reference/kotlin/android/app/Application.html)'s `onCreate()` method. You must also use the application context at this step:

``` kotlin
class MyApplication : Application() {
   override fun onCreate(){
        super.onCreate()
        
        // Specify the class that will hold your translations. 
        // It is regenerated at build time and you will use it to access your strings.
        NStack.translationClass = Translation::class.java
        
        // initilize the SDK with the application object
        NStack.init(this)
   }
}
```

You can also set several **optional** parameters if you need more control:

``` kotlin
// Enable debug mode for the library (outputs messages to log)
NStack.debugMode = true 

// Set a refresh period for NStack to check for updates
NStack.setRefreshPeriod(60, TimeUnit.MINUTES) 
```

> Warning: In almost every instance you want to set these optional methods before NStack is initialized

## Activity configuration

You have to attach NStack to each activity you're planning on using it in.

``` kotlin
override fun attachBaseContext(newBase: Context) {
    super.attachBaseContext(NStackBaseContext(newBase))
}
```

Please note the `NStackBaseContext` wrapper being attached in the snippet.

