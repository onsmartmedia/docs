AD.app Development
===================

The AD.app Concept
-------------

AD.app is ON Smart Media’s groundbreaking active and interactive advertising solution. AD.apps are Android applications developed specifically for the purpose of engaging the public.

AD.app Types
-------------
Only native Java Android applications are currently recommended. Applications created in platforms such as Phonegap or Appcelerator are supported but not recommended.
 
Development Process
-------------

To develop applications for ON Smart Media’s displays:

1. Download and install Android Studio per the guidelines from the Android developer site. Follow instructions as per Android Studio (https://developer.android.com/studio/install.html) to set up your IDE (Integrated Development Environment). 
2. Build your application:
  * full-screen theme
  * target API level 18
  * place icon in drawable folder
  * set proper screen resolution (Ex: 1080 x 1920)

3. Create an AVD for the appropriate ON display size. 
  * Genymotion
  * AVD manager
  * To create a Virtual machine, you can use the IDE shown above. 
4. Submit application to your designated ON Smart Media contact. 
  * Ensure your submission increments the VersionCode of your Android manifest each time you submit to OFM.
  * Provide ON Smart Media with any URLs accessed by your networking code for whitelisting purposes required in some installations.

Development Notes
-------------
#### Restrictions
 - Application frameworks such as Phonegap, Cordova or Appcelerator are not recommended as these applications may have unpredictable graphics performance, such as flickers or delays.

 - Display and touchscreen applications only. Some sites support sound and camera capabilities through the standard Android APIs. Touchscreen-enabled devices will receive input events through normal Android channels.

 - Native widgets such as keyboard, text input, date picker, test fields, and similar are not available

 - Google Play services and any SDK dependent on Google Play services is not supported. No Google services, such as Google Maps or Google Now, are available.

 - AD.app developers are required to sign their APKs. Unsigned APKs will be rejected. Self-Signed applications are acceptable.

 - Don’t use splash screens

 - Don’t lock orientation of the application 
 
> **Note:** Only the following permissions may be used: 

Permission     | Purpose
-------- | ---
ACCESS_COARSE_LOCATION | Allows application to access approximate location 
ACCESS_NETWORK_STATE     | Allows application to access information about networks Protection level: normal
INTERNET     | Allows application to access the Internet
CAMERA     | Allows application to access the camera
USB_PERMISSION     | Allows application to access USB peripherals

#### Activity Lifecycle
**Thread Handling**
 - Avoid UI updates when AD.apps go onPause
 - Remove all threads (Timer, Runnable, Thread) when the AD.app goes onPause. Exception: unless the thread will not communicate to the activity.

**Caching**
 - For performance reasons, Fragment use is strongly recommended instead of multiple Activities
 - Use UI caching, to store current UI status
 - Use socket call caching, to store the last call and returned result (Ex: HTTP, API call, UDP). Note that network connections may rely on 3G (not 4G) networks and can occasionally experience frequent outages and drops. AD.apps must be designed to function properly with intermittent network connectivity..
 - Any video content must be preloaded to RAM and fully realized before playback to ensure synchronized content.

**Screen Resolution**
Ensure that the AD.app is designed to the resolution and orientation of the specific display

The following resolutions/orientations are supported. **Note:** At this time, the screens do not rotate.
 - 1080 (w) x 1920 (h) (portrait)
 - 1920 (w) x 1080 (h) (landscape)
 - 1440 (w) x 1920 (h) (square)
 - 1200 (w) x 1920 (h) with visible area of 1648 (w) x 1184 (h) (1500 Broadway billboard)

Application Icons
-------------
 - Include an application icon in the SDK 144px x 144px in .PNG format.
 - Applications are displayed using the mdpi asset bucket. 


Performance and Testing Guidelines
-------------
 - SD Card Storage: 32 Gb for each display, with approximately 28 Gb usable capacity.
 - Storage usage: The installed application plus associated data should not exceed more than 500 Mb of persistent storage.
 - Memory usage: Application memory usage should not exceed 60 Mb.
 - The Android platform scores approximately 13,000 on the AnTutTu (tm) benchmark v5.7.1 if you do not have access to hardware to develop your application, use commercial tablets with comparable performance running Android 4.3. As an example, you may test using a 2013 era Nexus 7 Tablet: http://www.antutu.com/view.shtml?id=1282 

Coding Guidelines
-------------
 - Handle all threads in Activity-Lifecycle:
 - Handle all removing/pausing threads in onPause
 Example:, timer, runnable, thread, bus
 ```
if(timer != null)

    timer.cancel();

if(runnable != null)

    handler.removeCallbacks(runnable);

if(bus != null)

    bus.unregister(this);
@Override

protected void onPause()

{
    super.onPause(); 

}
handle all resuming thread in onResume()
if(timer == null)

    timer.start();

if(runnable != null)

    handler.post(runnable);

if(bus != null)

    bus.register(this);
@Override

protected void onResume()
{ super.onResume(); }
```

Example AD.Apps
-------------
 - HelloWorld example: https://github.com/onsmartmedia/ExampleProjects/tree/master/HelloWorld
 - Threads example: https://github.com/onsmartmedia/ExampleProjects/tree/master/HelloWorldThread
 - Caching example: https://github.com/onsmartmedia/ExampleProjects/tree/master/HelloWorldCache

AD.App Submission Process
-------------
Deliver your AD.app to your sales contact at ON Smart Media. The ON Smart Media team will test your application thoroughly to ensure it meets the technical and performance guidelines stated above. 

