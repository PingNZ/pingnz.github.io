---
title: 'Mac OS X Development Tutorial for Beginners Part 1: Intro to Xcode'
date: 2017-01-23 12:30:20
tags: Swift
categories: IT相关

---
Want to learn how to develop your own apps for Mac OS X?

Good news – Apple makes developing for OS X incredibly easy – and in this tutorial series we’ll show you how. You’ll learn how to create your first app for OS X – even if you’re a complete beginner.

1. In this first part you’ll first learn about how to obtain the tools you need to develop for OS X. Then, using an app you’ve downloaded as an example, you’ll take a tour of Xcode, discovering how to run an app, edit code, design the UI and debug it.
2. In part two, you’ll take a step back from Xcode to learn about the components that make up an OS X app. From how an app starts, through how the UI is constructed all the way to handling user interaction.
3. You’ll get your hands dirty in the final part – building your first ever OS X app. Starting from nothing, you’ll soon have a simple app up and running on your mac!


So what are you waiting for? The world of desktop apps awaits!

> Note: Here’s some guidance of where to begin with this series:
> 
* **If you are new to Swift,** this series assumes Swift knowledge, so first check out our [Swift tutorials](http://www.raywenderlich.com/category/swift) to get a great introduction.
* **If you already have iOS experience,** this first part of the series will be review. Take a quick look through the topics to make sure and then skip straight ahead to the [next part of the series](http://www.raywenderlich.com/110267/mac-os-x-development-tutorial-for-beginners-part-2-os-x-app-anatomy).
* **Otherwise,** keep reading – this series is for complete beginners – no experience of developing for iOS or OS X is required!

# Prerequisites
To become an OS X developer, you will need a few things:

* **Mac running OS X.** The OS X operating system only runs on Apple computers, so you need a Mac both to develop and run OS X apps. If you’re wondering which Mac to buy, we recommend a Mac Mini with extra memory and a solid state or Fusion drive; it’s the best balance between cost and power.
* **An AppleID.** In order to download the tools from the App Store, you’ll need an AppleID.
* **Xcode.** This is the IDE and toolchain used to create OS X apps. You’ll learn how to install this in the next section.

Once you’ve built your app, and you want to upload it to the App Store to be distributed, you’ll also need to pay for an Apple developer account. But this is not a requirement until you are ready to send your app out to the world.

# Obtaining Tools
Unlike some other platforms, developing for OS X requires the installation of one tool – known as Xcode. Xcode is an IDE that includes everything you need to develop iOS, watchOS and OS X apps.

If you don’t have Xcode already, click on the Apple icon in the upper left of your menu and select App Store to open the Mac App Store.

![](https://koenig-media.raywenderlich.com/uploads/2015/08/AppStore21.png)

Search for Xcode and download it:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/xcode_mas-679x500.png)

Once it has downloaded and installed, open Xcode from your Applications folder. The first time you open Xcode it’ll ask to install some additional components. Go ahead and let it, entering your password if required.

You’ll then be presented with the Xcode welcome screen:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/xocde_welcome-480x289.png)

Congratulations, you’ve successfully installed Xcode! Read on to learn all about what it can do.

## Beta versions of Xcode

Before moving on to describing the power of Xcode, it’s worth taking a few minutes learning about beta versions of Xcode.

When Apple releases new updates to Xcode (often to support new features in OS X, iOS and watchOS) they go through an agressive cycle of beta releases. These releases include the new features, but consequently many bugs. If you are interested in developing an app which leverages these new features, you’ll need to download the latest beta from Apple.

This tutorial requires Xcode 7, since the sample project used in this tutorial has been updated to the Swift 2.0 programming language. There are two cases:

* **If the App Store version of Xcode is Xcode 7 at the time of reading this tutorial,** you are all set!
* **If the App Store version of Xcode is Xcode 6 at the time of reading this tutorial,** you’ll need to install a beta version of Xcode 7 – keep reading to learn how.

To get the latest beta version of Xcode, visit [developer.apple.com](https://developer.apple.com/), click on **Resources, Xcode,** and then Download. Follow the link to **download** the latest version of Xcode beta there.
Note you can install a beta version of Xcode alongside the stable version, so there’s no problem with continuing work on projects that aren’t ready for upgrade.

![](https://koenig-media.raywenderlich.com/uploads/2015/08/XcodeBeta.png)

The download is a DMG, so you can install by dragging the Xcode app across into **Applications** in the usual way. You’ll then have two versions of Xcode in your applications folder:

![](https://koenig-media.raywenderlich.com/uploads/2015/08/2Xcode.png)

Run **Xcode-beta** and then you’re ready to continue on!

**Hello World!**

Xcode is an Integrated Development Environment (IDE) which means that it is a collection of all the tools you need, from source code editing, compilation through to debugging and UI design.

When you open Xcode it allows you to create a new project, or open an existing one. You can also open an existing project by double clicking on an Xcode project or workspace in Finder:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/open_finder-480x269.png)

## Creating a new app
For most of this tutorial you’ll tour Xcode via a sample app, but first things first – you can’t start learning about a new platform without first creating a “Hello World” app!

To do this, select **Create a new Xcode project** from the Xcode welcome screen:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/xocde_welcome-480x289.png)

The template chooser allows you to decide how Xcode will configure your new project. In the O**S X \ Application** section you can see the three different core OS X app types:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/new_project-451x320.png)

The three different app types are as follows:

* **Cocoa Application:** An OS X desktop app – with a window-based UI. Cocoa is the name of the framework upon which all OS X applications are built.
* **Game:** Games built using Apple’s SpriteKit or SceneKit frameworks.
* **Command Line Tool:** A utility that runs in a shell, and has a text-based UI.

Select **Cocoa Application,** and click **Next**. On the screen that follows, set the **Product Name **to **HelloWorld**, check the language is set to **Swift** and that **Use Storyboards **is checked:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/new_project1-450x320.png)

Click **Next**, and choose a location on disk to save your project.

This creates a new, empty project ready for you to craft into your amazing app. The first thing you’ll want to do is build and run it to check that it’s all working.

## Running your app
Whether you’ve opened an existing app or created a new one, the most important thing you’ll want to do is to build and run it.

This involves compiling all of the code you’ve written into machine code, bundling up the resources required by the app and then executing it. This process is complex, but luckily Xcode has your back. To build and run your project simply press the **play** button on the toolbar:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/play_button1-480x124.png)

You can also build and run your app with the **⌘R** keyboard shortcut.

![](https://koenig-media.raywenderlich.com/uploads/2015/07/bar_empty-480x292.png)

>**Note**: The first time you ever build and run an app in Xcode, you might well be asked whether you want to **Enable Developer Mode on this Mac?.** You’re safe to select **Enable**, at which point you may have to enter your password. Developer mode allows Xcode to attach a debugger to running processes – which will be extremely useful when building your application!

Your **HelloWorld** app is currently looking a bit empty – and doesn’t even say hello! You’re going to fix that now.

## Adding Text

You’re going to update the user interface (UI) of your app to make it into a true “Hello World” app, and to do this you’re going to use a tool called Interface Builder (IB). You’ll learn much more about Interface Builder later in this tutorial – for now, you just need to know enough to add some text to the layout.

Find the **Main.storyboard** file in the **Project Navigator,** and click on it:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/open_storyboard-294x320.png)

This opens the storyboard file in Interface Builder – you can see an outline of your entire app:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/hello_world_storyboard-343x500.png)

The lower component (entitled “View Controller”) represents the visual appearance of your app. You’re going to add a text label to this to create your “Hello World” app.

Find the **Object Library** in the lower right part of the Xcode window. Type **label** into the search box and locate the **Label** entry:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/object_library-330x320.png)

**Drag** a label from the **Object Library** onto the empty **View Controller** scene canvas:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/drag_label-480x312.png)

A label represents a static piece of text – with no user interaction – perfect for your Hello World app. You don’t want it to say “label” though – you’re going to update that next.

To configure the label, select it and then open the **Attributes Inspector **(the 4th tab) on the right hand side of the Xcode window. Set the **title** to **“Hello OS X!”**, and update the **font** to be s**ize 40:**

![](https://koenig-media.raywenderlich.com/uploads/2015/07/label_config-296x320.png)

You may see that the label is no longer sized correctly – next you’ll fix that and set it to the correct position.

You position UI elements in OS X using a system called Auto Layout – which allows you to specify positions and sizes of UI elements in terms of their relationships. You want to put your “Hello OS X!” label in the center of the window – so you’re going to add constraints to achieve this.

Select the label once again, and click the **Align** button in the bottom bar (the second from the left). Check both the **Horizontally in Container** and the **Vertically in Container** boxes, and ensure that they are both **set to 0**. Select **Items of New Constraints** in the **Update Frames** selection box before finally clicking the **Add 2 Constraints button:**

![](https://koenig-media.raywenderlich.com/uploads/2015/07/constraints-413x320.png)

This will update the storyboard to position and size your label correctly.

Build and run your app (either by clicking the play button, or using the **⌘R** keyboard shortcut) to see your “Hello World!” Mac OS X app:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/hello_osx-480x293.png)

# Introducing HubEvent
You’ll continue learning how to make projects from scratch and code OS X apps in later parts of this series, but for the rest of this tutorial you’ll focus on learning more about Xcode itself.

To help with that, I’ve created a sample project for you called **HubEvent** that you’ll work with for the rest of this tutorial. This way you can get a tour of Xcode with a real-world project.

[Download](https://koenig-media.raywenderlich.com/uploads/2015/11/HubEvent_7.1.zip) the **HubEvent** starter project, unzip it and **double click** on **HubEvent\HubEvent.xcodeproj **in Finder to open it in Xcode.

Build and run **HubEvent** sample project and you’ll see it compile and then launch:

![](https://koenig-media.raywenderlich.com/uploads/2015/07/hubevent-613x500.png)

HubEvent uses the public GitHub API to pull down all the events for a user, and displays a summary of them in a table. As you select each row of the table, the raw JSON associated with that event is displayed in the panel below.

# Xcode Core Functionality
HubEvent is a fairly simple app, but is complex enough to demonstrate the core functionality of Xcode. The remainder of this tutorial will cover the following:

* **Code Editor.** All OS X apps have a code component, and HubEvent is no different. The code in HubEvent is responsible for downloading the data from the GitHub API, and wiring it up to the user interface.
* **Interface Builder.** You’ve already used Interface Builder when you build your “Hello World!” app. You’ll learn more about how this powerful tool allows you to build up the split-window UI used in HubEvent.
* **Asset Catalog. **All image assets are stored inside asset catalogs – you’ll discover how to replace the standard app icon with something more interesting.
* **Debugging.** Everybody makes mistakes when writing code and building apps and Xocde’s debugger makes identifying and fixing bugs a whole lot easier.
* **Documentation.** OS X apps are build on top of some extremely advanced system frameworks, and nobody can remember exactly how to use each and every one of them. Luckily Apple creates high-quality documentation and has integrated it with Xcode to make it easy to find answers to your questions.
## Code Editor
Apps are built primarily from code, written in the Swift programming language. You can also use Objective-C to write apps for OS X, but Apple introduced Swift in 2014, and was very clear that it is the langauge of the future. **HubEvent** is written in Swift.

One of the views available in Xcode is the **Code Editor,** which is activated whenever you open a source code file. To see it, select **WindowController.swift** from the **Controllers** group in the **Project navigator.**

![](https://koenig-media.raywenderlich.com/uploads/2015/07/source_editor-700x368.png)

>**Note**: You might need to show the Navigator pane on the left hand side using the buttons in the toolbar, and choose the Project navigator within the navigator pane. The buttons are shown in the above screenshot.