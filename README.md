# SealedApiResults
[ ![Download](https://api.bintray.com/packages/nhaarman/maven/SealedApiResults/images/download.svg) ](https://bintray.com/nhaarman/maven/SealedApiResults/_latestVersion)

SealedApiResults utilizes Kotlin's sealed classes to provide a safe way of handling http network calls.

## Example

```kotlin
fun onResult(result: SealedApiResult<String>) =
    when(result) {
      is Ok200 -> println(result.body)
      is Unauthorized401 -> println("Unauthorized")
      is Some -> println("Unhandled response: ${result.code}")
      is NetworkError -> result.e.printStackTrace()
    }
```

The compiler will complain when you forget to handle a case, such as the `NetworkError`.
This makes for a very safe way of dealing with network results.

## Install

SealedApiResults is available on JCenter.
For Gradle users, add the one of the following 'compile' sections to your `build.gradle`:

```groovy
repositories {
    jcenter()
}
dependencies {
    compile "com.nhaarman:sealedapiresults:x.x.x"
    compile "com.nhaarman:sealedapiresults-retrofit:x.x.x"
    compile "com.nhaarman:sealedapiresults-retrofit-rx:x.x.x"
}
```

### Kotlin 1.1-M01

Kotlin version `1.1-M01` relaxes rules for sealed classes and data classes.
To include a version that uses `1.1-M01`, use one of the following:

```groovy
repositories {
    jcenter()
}
dependencies {
    compile "com.nhaarman:sealedapiresults-kt1_1-M01:x.x.x"
    compile "com.nhaarman:sealedapiresults-retrofit-kt1_1-M01:x.x.x"
    compile "com.nhaarman:sealedapiresults-retrofit-rx-kt1_1-M01:x.x.x"
}
```
