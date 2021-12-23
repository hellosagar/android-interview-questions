# Android interview questions that I've faced so far or I think is important

 > I'm creating this repository after getting rejected from ShareChat

## Android Components
### Explain briefly all the Android application components

**App components** are the essential building blocks of an Android app. Each component is an entry point through which the system or a user can enter your app.
There are four different types of app components :

* **Activities** - An activity is the entry point for interacting with the user. It represents a single screen with a user interface.
* **Services** - A service is a general-purpose entry point for keeping an app running in the background for all kinds of reasons. It is a component that runs in the background to perform long-running operations or to perform work for remote processes.
* **Broadcast receivers** - A broadcast receiver is a component that enables the system to deliver events to the app outside of a regular user flow, allowing the app to respond to system-wide broadcast announcements.
* **Content providers** - A content provider manages a shared set of app data that you can store in the file system, in a SQLite database, on the web, or on any other persistent storage location that your app can access.

### What is an Activity?

An **activity** provides the window in which the app draws its UI. This window typically fills the screen, but may be smaller than the screen and float on top of other windows. Generally, one activity implements one screen in an app. For instance, one of an app’s activities may implement a Preferences screen, while another activity implements a Select Photo screen.

--------------
## Activity Lifecycle
### Activity Lifecycle (in execution order) -

| Method  | Called When  |
|---|---|
| onCreate()   | Activity is first created.  |
| onStart()    | Activity is becoming visible to the user.  |
| onResume()   | Activity will start interacting with the user.  |
| onPause()    | Activity is not visible to the user.  |
| onStop()     | Activity is no longer visible to the user.  |
| onRestart()  | After activity is stopped, prior to start.  |
| onDestroy()  | Before activity is destroyed.  |

 >*Note - The onCreate() and onDestroy() methods are called only once throughout the activity lifecycle.


### Uses case of activity lifecycle with execution order

##### **When activity is opened:**
```kotlin
onCreate()

onStart()

onResume()
```
##### **When moved to another activity:**
> Here A == first activity and B == second activity

```kotlin
onPause() - (A)

onCreate() - (B)

onStart() - (B)

onResume() - (B)

onStop() - (A)
```

##### **When another activity is closed and moving back to first activity:**

```kotlin
onPause() - (B)

onRestart() - (A)

onStart() - (A)

onResume() - (A)

onStop() - (B)

onDestroy() - (B)
```

### onStart vs onResume
**onStart()** -> called when the activity becomes visible, but might not be in the foreground (e.g. an AlertFragment is on top or any other possible use case).

**onResume()** -> called when the activity is in the foreground, or the user can interact with the Activity.

### onPause vs onStop
**onPause()** -> If you can still see any part of it (Activity coming to foreground either doesn't occupy the whole screen, or it is somewhat transparent).

**onStop()** -> If you cannot see any part of it


A dialog, for example, may not cover the entire previous Activity, and this would be a time for onPause() to be called


## 5 Anti patterns in android
- **Using base classes**: Causes the tight coupling
- **Putting all dependencies in AppModule**: Hard to read and during testing, we can't get the specific module
- **Using one activity per screen**: Activity is heavy as it uses intent to open which internally talks to the android system and the fragment is similar to displaying a layout.
- **Hardcoding dispatchers**: It forces the coroutine to use the particular dispatcher whereas in testing we need to pass the test dispatcher.
- **Using GlobalScope**: Its keeps running during the application process and doesn't care about the lifecycle of the component which causes memory leak or dead object exception.

Thanks to Philipp Lackner for making a video on this - <a href="https://www.youtube.com/watch?v=skW4wSuXCe0">Link</a>


## 6 Design pattern every android developer must know
- Singleton
- Factory
- Builder
- Facade
- Dependency Injection
- Adapter

Thanks to Philipp Lackner for making a video on this - <a href="https://www.youtube.com/watch?v=4cCwuBsqfTI">Link</a>


## SOLID stands for:
S - Single-responsiblity Principle

O - Open-closed Principle

L - Liskov Substitution Principle

I - Interface Segregation Principle

D - Dependency Inversion Principle

> Summary: We can say that the Single Responsibility Principle is about actors and high level architecture. The Open/Closed Principle is about class design and feature extensions. The Liskov Substitution Principle is about subtyping and inheritance. The Interface Segregation Principle (ISP) is about business logic to clients communication. And the Dependency Inversion Principale (DIP) is about leads or helps us respect all the other principles.

Thanks to Abderrazak Laanaya for writing a article on this - <a href="https://medium.com/android-news/android-development-the-solid-principles-3b5779b105d2">Link</a>

## General Questions

- Tell me about <a href="https://developer.android.com/jetpack">Jetpack Libraries </a>
- Why shoud we use an app architecture and what are the best practices? <a href="https://medium.com/oceanize-geeks/android-application-architecture-189b4721c7c5">read</a> 
- What are Services, Broadcast receivers and Content providers? <a href="https://developer.android.com/guide/components/fundamentals">read</a>
- Tell me about the Manifest file, what is it's role? <a href="https://developer.android.com/guide/components/fundamentals#Manifest">read</a>
- Difference between const and val? - val variable is initialized at runtime and const at compile time. Read more <a href="https://blog.mindorks.com/what-is-the-difference-between-const-and-val">here</a>
- Diffrence between sp and dp - sp is same as dp, just android resizes it based on font size set by user.
- What are diffrent Launch modes in android? <a href="https://medium.com/mindorks/android-launch-mode-787d28952959">read</a>
- What are implicit and explicit intents? <a href="https://stackoverflow.com/questions/2914881/android-implicit-intents-vs-explicit-intents">read</a>
- What makes kotlin the best language for native development? <a href="https://kotlinlang.org/docs/comparison-to-java.html">read</a>
- Explain the internal working of a RecyclerView. <a href="https://blog.mindorks.com/how-does-recyclerview-work-internally">read</a>
- On which thread would you update the UI components?- Main thread.
- What are companion objects? <a href="https://medium.com/swlh/kotlin-basics-of-companion-objects-a8422c96779b">read</a>
- Fragment lifecycle <a href="https://developer.android.com/guide/fragments/lifecycle">read</a>
- What are the diffrences between MVVM, MVC and MVP? <a href="https://blog.mindorks.com/mvc-mvp-mvvm-architecture-in-android">read</a>
- How would you implement DI in your preferred architechure.
- How is Interface useful in your architechure.
- How to interact with other apps? <a href="https://developer.android.com/training/basics/intents">read</a>
- How to use vibration in our app? <a href="https://www.geeksforgeeks.org/how-to-vibrate-a-device-programmatically-in-android/">read</a>
- Tell me about <a href="https://developer.android.com/training/dependency-injection">Dependency Injection</a>
- What is NDK and why is it used?<a href="https://stackoverflow.com/questions/6660621/what-is-the-android-native-development-kit-ndk">read</a>
- What is the diffrence between .apk and .aab? <a href="https://stackoverflow.com/questions/52059339/difference-between-apk-apk-and-app-bundle-aab">read</a>
- What is databinding? <a href="https://developer.android.com/topic/libraries/data-binding">read</a>
- What is a multi-modular app? <a href="https://proandroiddev.com/modularization-of-android-applications-in-2021-a79a590d5e5b">read</a>
- What is KAPT? <a href="https://mdapp.medium.com/annotation-processing-with-kapt-and-gradle-237793f2be57">read</a>

## What is expected that you know
- Basics of oops classes, inheritance, encapsulation, polymorphism and all of that stuff
- Basic Data sturctures knowledge and problem solving skills 
- Basics of Database (eg SQL)
- Basic Operating System knowledge (eg. Threads, cpu scheduling) 
- Basic Computer Science curriculum knowledge
- <a href="https://www.tutorialspoint.com/design_pattern/design_pattern_quick_guide.htm">Design patterns</a>
