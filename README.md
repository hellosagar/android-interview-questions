# android-interview-questions that I've faced so far or I think important

 > I'm creating this repository after getting rejected from ShareChat


### Activity Lifecycle (in execution order) -

**onCreate()** -	called when activity is first created.

**onStart()** -	called when activity is becoming visible to the user.

**onResume()** -	called when activity will start interacting with the user.

**onPause()** -	called when activity is not visible to the user.

**onStop()** -	called when activity is no longer visible to the user.

**onRestart()** -	called after your activity is stopped, prior to start.

**onDestroy()** -	called before the activity is destroyed.


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



