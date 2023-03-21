# flutterfire-login

A Flutter project with Firebase focused on [google_sign_in](https://github.com/flutter/packages/tree/main/packages/google_sign_in), based on [its example code](https://github.com/flutter/packages/tree/main/packages/google_sign_in/google_sign_in/example).

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

## Run

```
flutter pub get
flutter run -d chrome  --web-port 5000
```

## Setup Notes

### Notes for Web 

- The code needs to set the `clientId` in [index.html](web/index.html) which is obtained from Firebase
- We need to run the web server at authorized javascript origins which normally is  http://localhost:5000 during testing
  - Run `flutter run -d chrome  --web-port 5000` to launch the app during testing
  - If testing remotely, we could build the web app and then launch it with `python -m http.server 5000`
- Finally, the code needs to access user's contact and this won't work until we enable the [Google People API](https://console.developers.google.com/apis/api/people.googleapis.com/overview?project=839148412972) 


### Notes for Android

- Run `./gradlew signingReport` from the `android` folder to get app fingerprints
- Copy and Paste the SHA1 and SHA-256 fingers to [Firebase Project Settings for Android](https://console.firebase.google.com/project/flutterfire-3d3b0/settings/general/android:com.example.googlelogin)
- Note that the client_id information is stored in [android/app/google-services.json](android/app/google-services.json) for Android.

## Notes for iOS

- [GoogleService-Info.plist](ios/Runner/GoogleService-Info.plist) needs to be added to xcode project and it contains the google oAuth ID.
- Value of `REVERSED_CLIENT_ID` needs to be set in [Info.plist](https://github.com/jinzishuai/flutterfire-login/blob/master/ios/Runner/Info.plist#L32)
