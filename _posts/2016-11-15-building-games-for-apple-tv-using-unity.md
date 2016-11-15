---
layout:     post
title:      Building games for Apple TV using Unity
date:       2016-10-18 12:31:19
summary:    The Apple TV platform (also known as tvOS) builds on the foundation of the iOS platform, but game content often needs to be adapted to work correctly with Unity’s new input controls and the fact that the game is displayed on a big screen.
author:     A SAI RAHUL
permalink:  /building-games-for-apple-tv-using-unity/
tags:
  - unity-tag
---

![desk](https://rawgit.com/blogofcode/blogofcode.github.io/master/images/slide-out-slidebar-menu/Screen%20Shot%202016-10-25%20at%2010.39.58%20PM.png)

Here I discuss how to set up project for tvOS platform and control GUI item focus.

### Prerequisites

* Xcode 7.1 or later.
* Apple TV Simulator or A 4th generation Apple TV device.
* If Apple TV device, you need to set up provisioning for this device in the same way as for iOS devices.

### Setting Up

First, we need to change platform to tvOS. Go to `File -> Build Settings`. Click on `tvOS` and Switch Platform.

Add GUI item to the scene by going to `GameObject -> UI` and let's say button.
Go to `Edit -> Project Settings -> Input` and in the `Submit` dropdown rename `Alt Position Button` to `joystick button 14`.

### Setup GUI item for focus

Next, we focus GUI item by adding `Event System` to Main Camera or Main Object in the scene.

* Click on Main Camera or Main Object.
* Add Component in the Inspector and select `Event System`.
* In the `First Selected` in the Event System(Script), add the GUI item you wish have focus on.
* Then click `Add Default Input Modules` in the same Event System(Script).
* And then check `Force Module Active` to the bottom.

### Using GUI Item Focus

Next, if you want focus GUI item and capture the touch event on it. You can add the following code:

{% highlight js %}
    Input.GetButtonDown("Submit")
{% endhighlight %}

This returns bool value(write it inside an if statement to use touch event). You can add it in Update() function so that when ever touch event on that GUI item is triggered, your code inside if statement gets executed.


Hope this helps the developers who are starting to create Apple Tv Apps using Unity.



---
