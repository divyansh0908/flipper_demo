
# React Native Flipper Integration

This repository contains a React Native boilerplate app with manual Flipper debugging configuration for React Native 0.73 and above. 

## Overview

With React Native 0.73, Flipper debugging support was officially deprecated from the core framework. This boilerplate demonstrates how to manually configure Flipper on the native Android side to restore its powerful debugging capabilities.

## Features

- Configured for React Native 0.73+
- Manual Flipper integration for Android
- Debug-only implementation to keep release builds clean
- Network monitoring capabilities
- Layout inspection support
- Organized debug utilities structure

## Prerequisites

- Node.js (18.x or newer)
- Java Development Kit (JDK) 17 (Zulu)
- Android Studio and Android SDK
- Flipper desktop app installed ([Download here](https://fbflipper.com/))

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/react-native-flipper-boilerplate.git
   cd react-native-flipper-boilerplate
   ```

2. Install dependencies:
   ```
   yarn install
   ```

3. Start the android app:
   ```
   npx expo run:android
   ```


## Flipper Configuration Details

### Key Files

- **android/app/src/main/java/com/flipperdemo/debug/FlipperUtils.kt**: Contains the Flipper initialization code
- **android/app/src/main/java/com/flipperdemo/MainApplication.kt**: Calls the Flipper initialization during app startup
- **android/app/build.gradle**: Contains the debug-specific Flipper dependencies

### Gradle Dependencies

The project uses build variants to include Flipper only in debug builds:

```gradle
dependencies {
    // Flipper dependencies only for debug builds
    debugImplementation 'com.facebook.flipper:flipper:0.271.0'
    debugImplementation 'com.facebook.soloader:soloader:0.10.5'
    debugImplementation 'com.facebook.flipper:flipper-network-plugin:0.271.0'

    
    // No-op version for release builds
    releaseImplementation 'com.facebook.flipper:flipper-noop:0.271.0'
}
```

## Using Flipper with This Boilerplate

1. Make sure you have the Flipper desktop application running
2. Launch your React Native app in debug mode
3. The app should automatically connect to Flipper
4. Enable the plugins you want to use (Network, Layout Inspector, etc.)

## Troubleshooting

- If Flipper doesn't connect, ensure the Flipper desktop app is running before launching your React Native app
- Verify that you're running a debug build of the app
- Check the Android logcat for any Flipper-related errors
- Make sure you're using compatible versions of Flipper libraries and the desktop app

## Alternative Debugging Tools

While this boilerplate focuses on Flipper integration, consider these alternatives:

- **Reactotron**: For state tracking and API monitoring
- **React Native Debugger**: All-in-one desktop debugging app
- **LogBox**: React Native's built-in logging system


## License

This project is licensed under the MIT License - see the LICENSE file for details.
