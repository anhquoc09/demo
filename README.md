# Integration React Native with Existing Apps

## Key Concepts

The keys to integrating React Native components into your Android application are to:

### [Step 1. Set up project directory structure and React Native dependencies.](https://github.com/anhquoc09/demo/tree/step1#step-1-set-up-project-directory-structure-and-react-native-dependencies)

1.1. Directory structure: Copy existing Android app to subfolder ```/android``` of React Native project.<br>

1.2. Install JavaScript dependencies:

- Create new ```package.json``` file in root directory of React Native project with content:

```json
{
  "name": "MyReactNativeApp",
  "version": "0.0.1",
  "private": true,
  "scripts": {
    "start": "yarn react-native start"
  }
}
```

- Install ```yarn```

```shell
npm install --global yarn
```

- Navigate to the directory with your ```package.json``` file and run command:

Install ```react-native```

```shell
yarn add react-native
```

Will see message like the following:

```
warning "react-native@0.52.2" has unmet peer dependency "react@16.2.0".
```

Then install ```react```

```shell
yarn add react@{version_print_above}
```

1.3. Adding React Native to Android app

- Configuration Maven: Add the React Native and JSC dependency to app's ```build.gradle```:

```groovy
dependencies {
    implementation "com.facebook.react:react-native:+" // From node_modules
    implementation "org.webkit:android-jsc:+"
}
```

- Add an entry for the local React Native and JSC maven directories to the top-level ```build.gradle```:

```groovy
allprojects {
    repositories {
        maven {
            // All of React Native (JS, Android binaries) is installed from npm
            url "$rootDir/../node_modules/react-native/android"
        }
        maven {
            // Android JSC is installed from npm
            url("$rootDir/../node_modules/jsc-android/dist")
        }
    }
}
```

- Enable native module autolinking:

Add the following to ```settings.gradle```:

```groovy
apply from: file("../node_modules/@react-native-community/cli-platform-android/native_modules.gradle"); applyNativeModulesSettingsGradle(settings)
```

Next add the following entry at the very bottom of the ```app/build.gradle```:

```groovy
apply from: file("../../node_modules/@react-native-community/cli-platform-android/native_modules.gradle"); applyNativeModulesAppBuildGradle(project)
```

- Configuring permissions: Make sure you have the Internet permission in ```AndroidManifest.xml```:

```xml
<uses-permission android:name="android.permission.INTERNET"/>
```

### [Step 2. Integrate a React Native app to Android app.](https://github.com/anhquoc09/demo/tree/step2#step-2-integrate-a-react-native-app-to-android-app)

### [Step 3. Run app and test the integration.](https://github.com/anhquoc09/demo/tree/step3#step-3-run-app-and-test-the-integration)

### [Step 4. Creating a release build in Android Studio.](https://github.com/anhquoc09/demo/tree/step4#step-4-creating-a-release-build-in-android-studio)