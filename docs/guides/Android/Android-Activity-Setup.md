## Activity Setup
Add this to whatever activity you are trying to use NStack in

```kotlin
override fun attachBaseContext(newBase: Context) {
    super.attachBaseContext(NStackBaseContext(newBase))
}
```

You just need to wrap your `BaseContext` with our custom wrapper.

