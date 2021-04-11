# Integration React Native with Existing Apps

## Key Concepts

The keys to integrating React Native components into your Android application are to:

### [Step 1. Set up project directory structure and React Native dependencies.](https://github.com/anhquoc09/demo/tree/step1#step-1-set-up-project-directory-structure-and-react-native-dependencies)

### [Step 2. Integrate a React Native app to Android app.](https://github.com/anhquoc09/demo/tree/step2#step-2-integrate-a-react-native-app-to-android-app)

### [Step 3. Run app and test the integration.](https://github.com/anhquoc09/demo/tree/step3#step-3-run-app-and-test-the-integration)

3.1 Apply the ```usesCleartextTraffic``` option to ```AndroidManifest.xml``` for Debug build,
it is disabled by default in Android API >= 28 and prevent connecting to [Metro bundler](https://facebook.github.io/metro/docs/getting-started/):

```xml
<application
  android:usesCleartextTraffic="true" tools:targetApi="28" >
  <!-- ... -->
</application>
```


3.2 Install [Metro bundler](https://facebook.github.io/metro/docs/getting-started/) and run Metro server to build ```bundle```:

- Run the following command to install Metro:

```shell
npm install --save-dev metro metro-core
```

or

```shell
yarn add --dev metro metro-core
```

- Start Metro server:

```shell
npm start
```

or

```shell
yarn start
```

or

```shell
react-native start
```

3.3 Run Android app:

- Run from terminal:

```shell
react-native run-android
```

- Or run normally with Android Studio

### [Step 4. Creating a release build in Android Studio.](https://github.com/anhquoc09/demo/tree/step4#step-4-creating-a-release-build-in-android-studio)