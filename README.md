# Firebase Cloud Messaging

## Add a Firebase configuration file :
In your root-level (project-level) Gradle file (build.gradle), add rules to include the Google Services Gradle plugin. Check that you have Google's Maven repository, as well.
```
buildscript {

  repositories {
    // Check that you have the following line (if not, add it):
    google()  // Google's Maven repository
  }

  dependencies {
    // ...

    // Add the following line:
    classpath 'com.google.gms:google-services:4.3.10'  // Google Services plugin
  }
}

allprojects {
  // ...

  repositories {
    // Check that you have the following line (if not, add it):
    google()  // Google's Maven repository
    // ...
  }
}
```
In your module (app-level) Gradle file (usually app/build.gradle), apply the Google Services Gradle plugin:
```
apply plugin: 'com.android.application'
// Add the following line:
apply plugin: 'com.google.gms.google-services'  // Google Services plugin

android {
  // ...
}

```

Add Firebase SDKs to your app :
```
dependencies {
    // Import the BoM for the Firebase platform
    implementation platform('com.google.firebase:firebase-bom:29.0.0')

    // Declare the dependencies for the Firebase Cloud Messaging and Analytics libraries
    // When using the BoM, you don't specify versions in Firebase library dependencies
    implementation 'com.google.firebase:firebase-messaging'
    implementation 'com.google.firebase:firebase-analytics'
}
```

Edit your app manifest :
```
<service
    android:name=".java.MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```
<br> 
<img width="1440" alt="Screen Shot 2021-11-23 at 16 44 48" src="https://user-images.githubusercontent.com/48391281/143037566-996e5ef8-1221-4186-868d-8943fb3e268f.png">
<br>

Screenshots of the app : <br><br>
<img width="342" alt="Screen Shot 2021-11-23 at 16 43 22" src="https://user-images.githubusercontent.com/48391281/143038835-49906f2d-6683-4804-a687-d9bce5b1c2c6.png">


<br> <br>
📄 Firebase Documents 👉🏼 https://firebase.google.com/docs/cloud-messaging/android/client


