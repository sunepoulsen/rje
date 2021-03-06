# Java Mobile Development Platform Abstraction for making library applications

Experimental prototype for mobile development infrastructure for DBC

Status: on-hold, better approach would probably be just to use microemu, and add support for GWT on that one.

## Goal: 

Portable layer on top of Java to target different mobile devices:

- HTML5 compliant devices (recent android, iphone, palm, ...) via GWT
- Non-HTML5-browsers via applet(+application)
- Android abstracted API
- Low end phones midlet via MIDP (only microemu in beginning)

API abstraction:

- Fullscreen canvas, with text and graphics

## TODO:

- Touch and keys as input methods. Capability querying.
- inputstream etc. on gwt
- resize/rotate-event
- HTTP(S) networking
- Basic JSON(+jsonp)
- simple storage
- read/load resource
- (Basic (JavaScript-like) scripting)
- (Basic XML+HTML)
- (iOS via xmlvm (can be generated from android source, native api perhaps later))

## Building:

### Fetch dependencies

    ./fetch-dependencies.sh

Takes a while...

### Build/run HTML5-app
  
    cd gwt
    ant devmode

### Build/run application/applet

    cd java
    mvn compile exec:java

### Build/run android-application

    ./depend/android-sdk-linux_x86/tools/android &
    xterm -e ./depend/android-sdk-linux_x86/platform-tools/adb logcat &
    cd android
    mvn install android:deploy

### Build/run microemu-version

    cd midlet
    ./run.sh
