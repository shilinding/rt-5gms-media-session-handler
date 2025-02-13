# 5G-MAG Reference Tools: 5GMS Media Session Handler 

This repository holds the 5GMS Media Session Handler implementation of the 5G-MAG Reference Tools.

## Introduction

The 5GMS Media Session Handler is an Android application that implements functionality for 5G Media
Streaming media session handling. It is implemented as an Android Messenger Service that
communicates via Inter Process Communication (IPC) with other Android libraries and applications
such as the Media Stream Handler and the 5GMS Aware Application.

The Media Session Handler communicates with the 5GMS Application Function via interface M5 to
establish and control the delivery of a streaming media session in the downlink direction. In
addition, the Media Session Handler exposes APIs via M6 to the 5GMS-Aware Application and to the
Media Player (for downlink streaming).

## Downloading

Release versions can be downloaded from
the [releases](https://github.com/5G-MAG/rt-5gms-media-session-handler/releases) page.

The source can be obtained by cloning the github repository.

```
cd ~
git clone https://github.com/5G-MAG/rt-5gms-media-session-handler.git
```

## Install dependencies
The 5GMSd Aware Application requires the [Common Android Library](https://github.com/5G-MAG/rt-5gms-common-android-library) to run.

It is included as Maven dependencies in the `build.gradle`:

````
dependencies {
   implementation 'com.fivegmag:a5gmscommonlibrary:1.0.0'
}
````

To install the dependencies follow the  installation guides in the Readme documentation of the project. Make sure to publish it as a local Maven repository:

* [Common Android Library](https://github.com/5G-MAG/rt-5gms-common-android-library#publish-to-local-maven-repository)

## Building

Call the following command in order to generate the `apk` bundles.

````
./gradlew assemble
````

The resulting `apk` bundles can be found in `app/build/outputs/apk`. The debug build is located
in `debug` folder the release build in the `release` folder.

## Install

To install the `apk` on an Android device follow the following steps:

1. Connect your Android device to your development machine
2. Call `adb devices` to list the available Android devices. The output should look like the
   following:

````
List of devices attached
CQ30022U4R	device
````

3. Install the `apk` on the target
   device: `adb -s <deviceID> install -r app/build/outputs/apk/debug/app-debug.apk`. Using `-r`
   we reinstall an existing app, keeping its data.

## Running

After installing the Media Session Handler application can be started from the Android app selection
screen.

As an alternative we can also run the app from the command
line: `adb shell am start -n com.fivegmag.a5gmsmediasessionhandler/com.fivegmag.a5gmsmediasessionhandler.MainActivity `

## Development

This project follows
the [Gitflow workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
. The `development`
branch of this project serves as an integration branch for new features. Consequently, please make
sure to switch to the `development`
branch before starting the implementation of a new feature. 