# NetworkSDK

NetworkSDK is a lightweight Android SDK for making HTTP requests easily in your Android applications.

## Installation

To integrate NetworkSDK into your Android project, follow these steps:

### Gradle

1. Open your root `build.gradle` file and add the Jitpack repository:

    ```groovy
    dependencyResolutionManagement {
        repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
        repositories {
            mavenCentral()
            maven { url 'https://jitpack.io' }
        }
    }
    ```

2. Then, add the dependency to your app's `build.gradle` file:

    ```groovy
    dependencies {
        implementation 'com.github.amanjn38:NetworkSDK:1.0'
    }
    ```

### Maven

1. Add the Jitpack repository to your `pom.xml` file:

    ```xml
    <repositories>
        <repository>
            <id>jitpack.io</id>
            <url>https://jitpack.io</url>
        </repository>
    </repositories>
    ```

2. Then, add the dependency to your `pom.xml` file:

    ```xml
    <dependency>
        <groupId>com.github.amanjn38</groupId>
        <artifactId>NetworkSDK</artifactId>
        <version>1.0</version>
    </dependency>
    ```

## Usage

### Integration in Your Android App

To use the NetworkSDK in your Android app, you can call the `executeRequest` function provided by the SDK.

```kotlin
private suspend fun executeRequest(
    url: String,
    endpoint: String,
    queryMap: Map<String, String>? = null,
    headers: Map<String, String>
): Resource<Response> {
    return try {
        val result = requestViewModel.executeRequest(url, endpoint, METHOD_NAME, queryMap, headers, body)
        result
    } catch (e: Exception) {
        Resource.Error("An error occurred: ${e.message}", null)
    }
}

Function Parameters

    url: The base URL for the HTTP request.
    endpoint: The endpoint to hit.
    queryMap (optional): A map containing query parameters.
    headers: A map containing HTTP headers