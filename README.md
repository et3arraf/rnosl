# react-native-open-settings

[![npm
version](https://badge.fury.io/js/react-native-open-settings@2x.png)](http://badge.fury.io/js/react-native-open-settings)

Open your apps settings in the Settings app :P

## Install

`npm install et3arraf/rnosl` or `yarn add et3arraf/rnosl`


### iOS
Open the app in Xcode then add `React Native Open Settings.xcodeproj` to the Libraries folder that you can find at the left under your project name. You can find `React Native Open Settings.xcodeproj` in `node_modules/react-native-open-source/`. 

### Android

- In `android/app/build.gradle` go to dependencies and add:
```
dependencies {
  ...
+ implementation project(':react-native-open-settings')
}
```

- In `settings.gradle`, add these lines:
```
+ include ':react-native-open-settings'
+ project(':react-native-open-settings').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-open-settings/android')
```

- If your react-native version is below 0.29.0 go to `MainActivity.java`, if it's >=0.29.0 then go to `MainApplication.java`. Both are under `android/app/src/main/java/com/<project name>/` and import the package
```
+ import com.opensettings.OpenSettingsPackage
```

Then register the sdk package in method getPackages()

```
    @Override
    protected List<ReactPackage> getPackages() {
        return Arrays.<ReactPackage>asList(
                new MainReactPackage(),
+                new OpenSettingsPackage()
        );
    }
    ...
}
```

## Usage

Require the `react-native-open-settings` module.

```
import OpenSettings from 'react-native-open-settings';
```

And then, where you want to open the settings, just do

```
// Check if location is enabled

OpenSettings.isLocationEnabled().then((isLocationEnabled) => {
  //isLocationEnabled is a boolean
})

// Open app permissions page 
OpenSettings.openAppPermissionsSettings()

// Open location settings page 
OpenSettings.openLocationSettings()

// Very fast country grabbing from locale settings
OpenSettings.getCountryCode().then((countryCode) => { 
  console.log(countryCode); // OUTPUT : US or LB or ...
})

// Very fast location grabbing. returns "none" if lastKnown result is null
OpenSettings.getLastKnownLocation().then((result) => { 
  console.log(result); 
})

```

Have fun!
