#  Welcome to the carnival

## Introduction

This is a part of the Udacity VR program. The task was to fixed various aspect for the carnival. 

### Version

Unity 2017.1.0p4
GVR Unity SDK v1.70.0


## Lessons

### Why is my app crashing?
I'm using an andriod phone galaxy S8 for this project. One issue I've encountered while trying to run my project on the phone was that the app would crash. The game was working fine from the Unity Editor though. Furthermore, I had preivous used the latest  versions of Unity and GVR and that deployed fine on my phone (I reverted to a earlier version because of the project restrictions).  So, my first inclination was to see the error it was giving me. But, I wasn't sure where the logs where. After some fruitless attempts trying to look at the system.so file, I found that the andriod sdk as a handy 'adb logcat' function which lets me look at the live acitivty logs of my phone. However, the next issue is that is just a raw feed of whatever is currently happening on the phone. So, I needed to find a way to fliter this strream. I found this hand [site](https://logmatic.io/blog/a-how-to-guide-to-debugging-with-android-logcat/) and this command.

```
adb logcat | grep -i "foo.example."
```

So, I greped for 'Unity' and noticed the bellow error

```
Could not recreate VR window because GfxDevice is in an invalid state
```

This lead me to [bug issue](https://github.com/googlevr/gvr-unity-sdk/issues/671). It turns out that until a month or 2 ago Cardborad apps where crashing on S8 phones if the phone wasn't set to WQHD+. Once I made this small setting change, the app worked fine!
