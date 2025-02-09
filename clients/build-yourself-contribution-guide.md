---
description: How to build the app on your own system, or how to contribute to the project
---

# Build Yourself / Contribution Guide

{% hint style="info" %}
This guide is tailored towards the Android Studio IDE. You can also build in VSCode, but some tools may not exist or may work differently.
{% endhint %}

## Pre-Requisites

* Install [Flutter](https://docs.flutter.dev/get-started/install), following the guide for your OS all the way up to the "Test Drive" page

## Build Instructions

### Initial Steps

1. Clone the repository to your system
   1. We recommend building off the `development` branch! It has the more recent code that is more likely to build without errors.
2. Add a blank file named `.env` to the root of the project directory. This is to prevent a build error.

### Android

1. Find `android > app > build.gradle` (not to be confused with `android > build.gradle`), and scroll down to `signingConfig signingConfigs.release` at line 111. Change this to `signingConfig signingConfigs.debug`.
2. In a terminal window at the root of the project directory, run `flutter build apk --release --flavor prod`
   * You may need to accept licenses and perform other tasks since you are building Flutter for the first time. The terminal output will guide you through this process.
3. The output APK file path will be given to you, simply transfer it to your phone and install it!

### Web

1. In `/lib/repository/models/html` add a new file called `giphy.dart`. Inside this, put only `const GIPHY_API_KEY = "";`. If you have your own API key for GIPHY, you can place it inside the quotes, otherwise leave it as is.
2. In the terminal window at the root of the project directory, run `flutter build web --web-renderer=canvaskit`. It will output the build files to `build/web` to be hosted on your server.

### Desktop

#### Windows Build

1. Install NuGet package manager
2. Go to Visual Studio Installer -> Modify Build Tools -> Individual Components and install the latest Windows 10 SDK
3.  Run the following commands:

    ```cmd
    flutter clean
    git reset
    flutter build windows
    ```

#### Linux Build

Under construction...

## Contribution Guide

Hey there! We're glad you want to contribute. We only ask for these three things:

1. Write clean code, and comment it!
2. Follow Flutter & Dart best practices
3. Avoid making large formatting changes to files, unless that is the goal of your PR. It makes it easier for us to review the changes this way.

### Get Started

Make sure you've completed [#pre-requisites](build-yourself-contribution-guide.md#pre-requisites "mention").

1. Fork the repo, and then clone the fork to your system
2. Open the files in the IDE of your choice
3. Complete step 2 of [#initial-steps](build-yourself-contribution-guide.md#initial-steps "mention")
4. Make your changes
5. Run the app using `flutter run` or the green play button at the top of your IDE
6. Test your changes
7.  Commit and PR!

    Make sure you don't commit your changes to comment out `onContentCommit`.

{% hint style="warning" %}
The client apps have a lot of variables that need to be tested. For example, if you're making a UI change, please make sure it looks good in all the default themes, and all the skins as well.

If you wish to make a backend change, we suggest you consult with the main developers before writing code. This is so we can come up with a plan of attack and make sure we don't degrade existing functionality or create bugs.
{% endhint %}

{% hint style="info" %}
Please create all PRs targeting the `development` branch, **not** the `master` branch.
{% endhint %}

{% hint style="info" %}
If you're new to Flutter development, look out for the `good-first-issue` or the `Difficulty: Easy` label on GitHub. These will be easier issues to help you start learning Flutter, without dealing with an overly-complex bug or feature.
{% endhint %}
