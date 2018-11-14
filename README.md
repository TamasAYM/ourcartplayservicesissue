# ourcart playservices issue

# Steps to reproduce:

1. check out the project
2. create and set up a firebase project so the google-services gradle
   plugin can run (more info at:
   https://firebase.google.com/docs/android/setup )
3. run `./gradlew build`

## expected result

project builds, no gradle error

## actual result

The issue is here: https://github.com/TamasAYM/ourcartplayservicesissue/blob/master/app/build.gradle#L38
 ```
In project 'app' a resolved Google Play services library dependency depends on another at an exact version (e.g. "[15.0.1]", but isn't being resolved to that version. Behavior exhibited by the library will be unknown.

Dependency failing: com.google.android.gms:play-services-flags:15.0.1 -> com.google.android.gms:play-services-basement@[15.0.1], but play-services-basement version was 16.0.1.

The following dependencies are project dependencies that are direct or have transitive dependencies that lead to the artifact with the issue.
-- Project 'app' depends onto com.google.firebase:firebase-core@16.0.5
-- Project 'app' depends onto com.google.firebase:firebase-config@16.1.0
-- Project 'app' depends onto com.ourcart:sdk@1.2
```
## additional information

as soon as we remove ourcart as a dependency the build succeeds

`// implementation 'com.ourcart:sdk:1.2'`