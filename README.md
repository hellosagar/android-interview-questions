# Android interview questions that I've faced so far or I think important

 > I'm creating this repository after getting rejected from ShareChat

## About Activity Lifecycle
### Activity Lifecycle (in execution order) -

**onCreate()** -	called when activity is first created.

**onStart()** -	called when activity is becoming visible to the user.

**onResume()** -	called when activity will start interacting with the user.

**onPause()** -	called when activity is not visible to the user.

**onStop()** -	called when activity is no longer visible to the user.

**onRestart()** -	called after your activity is stopped, prior to start.

**onDestroy()** -	called before the activity is destroyed.

Note - The onCreate() and onDestroy() methods are called only once throughout the activity lifecycle.

## Uses case of activity lifecycle with execution order

### When activity is opened:
onCreate()

onStart()

onResume()


### When moved to another activity:
> Here A == first activity and B == second activity
onPause() - (A)

onCreate() - (B)

onStart() - (B)

onResume() - (B)

onStop() - (A)

### when another activity is closed and moving back to first activity
onPause() - (B)

onRestart() - (A)

onStart() - (A)

onResume() - (A)

onStop() - (B)

onDestroy() - (B)

### onStart vs onResume
onStart() -> called when the activity becomes visible, but might not be in the foreground (e.g. an AlertFragment is on top or any other possible use case).

onResume() -> called when the activity is in the foreground, or the user can interact with the Activity.

### onPause vs onStop
onPause() -> If you can still see any part of it (Activity coming to foreground either doesn't occupy the whole screen, or it is somewhat transparent).

onStop() -> If you cannot see any part of it


A dialog, for example, may not cover the entire previous Activity, and this would be a time for onPause() to be called

## General Questions

1. Tell me about <a href="https://developer.android.com/training/dependency-injection">Dependency Injection</a>
2. Tell me about <a href="https://developer.android.com/jetpack">Jetpack Libraries </a>
3. Why shoud we use an app architecture and what are the best practices?<a href="https://medium.com/oceanize-geeks/android-application-architecture-189b4721c7c5">read</a> 
