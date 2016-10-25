---
layout:     post
title:      Slide Out Sidebar Menu
date:       2016-10-25 12:31:19
summary:    Slide-out navigation consists of a panel that slides out from underneath the left or the right of the main content area, revealing a vertically independent scroll view that serves as the primary navigation for the application.
categories: jekyll pixyll
author:     A SAI RAHUL
permalink:  /slide-out-slidebar-menu/
tags:
  - android
---

<!-- ![desk](https://github.com/blogofcode/blogofcode.github.io/blob/master/images/image-slideshow-using-viewpager-with-pageadapter/image_slideshow1.gif?raw=true) -->

In this article, we are going to create a slide-out navigation menu similar to the one you find in Facebook, Inbox, Digg, LinkedIn, etc. (Image Below). For that first we need to setup the `MainActivity` in which you want to include the image slideshow. Here we make use of an open source library `SWRevealViewController` to create sidebar menu.

### Using `SWRevealViewController` Library

Firstly, we need to [download the library from Github](https://codeload.github.com/John-Lluch/SWRevealViewController/zip/master). In the downloaded folder, you find two files: `SWRevealViewController.h` and `SWRevealViewController.m`. Add these two files by dragging them onto the Xcode project. As soon as you confirm to add the files, Xcode promts you to configure an Objective-C brindging header, by which you'll be able to access the Objective-C code from Swift. So click Yes to procedd.
image1
image2
Xcode genrates a header file named `projectname-Bridging-Header.h`. Open `projectname-Bridging-Header.h` file and add the followinf line to access the library in swift files.

`projectname-Bridging-Header.h`:
{% highlight objc %}

#import "SWRevealViewController.h"

{% endhighlight %}

### Front and Rear View Controllers

    * The front view controller is the main controller for displaying content.
    * The rear view controller is the controller that shows the navigation menu.
Next, in our `onCreate()` Activity method, we'll instantiate our custom `PagerAdapter` implementation and bind it to our `ViewPager` object.

In storyboard, first select the empty view controller and change the class to `SWRevealViewController`.

Next, control-drag from `SWRevealViewController` to the Menu View controller. After releasing the button, you will see a context menu for segue selection. I this case, select `reveal view controller set segue`. Then, select the segie and change its identifier to `sw_rear` under the Identity inspector on the right. This defines the side menubar.
    * Side menu bar which contains tableview(you can design the tableviewcell as you like) should be populated statically all by yourself.

Next, repeat the same procedure to connect `SWRevealViewController` with navigation controller of the news view controller. Again, select `reveal view controller set segue` when prompted and change the segue identifier to `sw_front`. This tells that navigation controller is the front view controller.
    * Front view controller should be the one you wish to see first. Go to `Editor->Embed In` ans select `Navigation Controller` to create navigation controller to the front view.
    * Add the menubar button to the left side of navigation bar.

### Slide View Gesture Recognizer

In our Front Vew Controller, insert the following lines of code:

{% highlight swift %}
    if self.revealViewController() != nil {
        menuButton.target = self.revealViewController()
        menuButton.action = #selector(SWRevealViewController.revealToggle(_:))
        self.view.addGestureRecognizer(self.revealViewController().panGestureRecognizer())
    }
{% endhighlight %}

In this, we first add reveal target to menubar button and then slide view gesture to reaveal rear view controller.
By this not only you can use the menu button to bring out the sidebar menu, you can swipe the content area to activate the sidebar as well.
Cool! Let’s compile and run the app in the simulator. Tap the menu button and the sidebar menu should appear. You can hide the sidebar menu by tapping the menu button again. You can also open the menu by using gesture. Try to swipe right on the content area and see what you get.

### Handling Menu Item Selection

Go back to storyboard. Select one tableviewcell and drag to the navigation controller of the view you want to reveal when that tableviewcell is clicked. Then, select `reveal view controller push controller` segue under selection segue. Do the same thing to all the view controllers' navigation view controllers.
    * Insert the above lines of code in all the view controllers you added to the menubar.

You can customize the menu by adding the following line of code to the front view controller:

{% highlight swift %}
self.revealViewController().rearViewRevealWidth = 62
{% endhighlight %}

If you run the app, you’ll have a sidebar menu like the one below. You can look into the SWRevealViewController.h file to explore the customizable options.

Hope you understand.

For those, who don't like to read but just copy the code, here's the [code](https://github.com/johnotander/pixyll).


---
