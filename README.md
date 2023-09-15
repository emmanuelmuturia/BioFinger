
# Experiment #10 (Bio)

## Overview
This is an Android application that demonstrates the implementation of Biometric Authentication (Fingerprint) in Jetpack Compose...

## Table of Contents

1. [BackGround](#Background)
2. [Procedure](#Procedure)
    1. [Setting Up The Dependencies](#Setting-Up-The-Dependencies)
    2. [Building The App](#Building-The-App)
    3. [Testing](#Testing)
3. [Trivia](#Trivia)

## Background
- This documentation seeks to provide a detailed, clear and resourceful guide on how to implement the Biometric (Fingerprint) functionality in Jetpack Compose...
- It is based on the Biometric API in Android...
- This app uses Jetpack Compose but the functionality borrows from the traditional approach...

## Procedure
To set up a similar app, here's what you need to do:

1. ### Setting Up The Dependencies
- This app uses the Biometric API to achieve the Biometric Authentication functionality...
- The API is implemented using the androidx.biometric library which was primarily focused on the XML way of doing things but can also be used in Jetpack Compose...
- To use it, add the following library to the app-level build.gradle.kts file:

```kotlin
implementation("androidx.biometric:biometric-ktx:1.2.0-alpha05")
```
- Add the following line to enable the Biometric permissions:

```xml
<uses-permission android:name="android.permission.USE_BIOMETRIC"/>
```

2. ### Building The App
- Depending on your use case, you can add Dependency Injection, Navigation etc...
- The core functionality would be the Biometric Authentication logic as that is the common denominator despite your app's architecture...
- The HomeScreen file has three main sections: HomeScreen, AuthenticationDialog, and myBiometricPrompt...
- HomeScreen represents the UI of the first screen, which consists of the Text and Button elements. The latter is used to invoke the Biometric Dialog/Prompt...
- AuthenticationDialog initiates the Biometric Authentication functionality...
- myBiometricPrompt is used to define and build the Biometric Dialog screen...
- It returns BiometricPrompt using the Biometric API...
- MainActivity has been set to extend FragmentActivity() instead of ComponentActivity() because BiometricPrompt requires its first parameter to be of type Fragment or FragmentActivity...
- Through the XML format we would have implemented the Biometric Authentication logic in another Fragment but in Jetpack Compose, we simply create a context object using LocalContext.current and cast it to FragmentActivity()...
- For the second parameter, we have converted an instance of CoroutineDispatcher to an implementation of Executor...
- An Executor is an object that executes submitted Runnable tasks. 
- This interface provides a way of decoupling task submission from the mechanics of how each task will be run, including details of thread use, scheduling, etc. 
- An Executor is normally used instead of explicitly creating threads.
- The third and final parameter of BiometricPrompt is the implementation of callbacks used depending on the Authentication result...

3. ### Testing
- To test the app, run and click the button...
- If the device has the Biometric (Fingerprint) functionality, you should see the dialog pop up after clicking the button...
- Once the authentication process is complete, the dialog should disappear and whatever functionality you implemented should follow up, which in this case is the navigation to the next screen...
- Here's the flow of screens:



## Trivia
- Google is yet to release an official API/Library that allows for an easy implementation of this functionality...
- This API was actually released mainly to aid in the Android Open Source Project's (AOSP) development...
- Testing this implementation is much more difficult in Jetpack Compose as we cannot individually test a Fragment unlike in the XML format...