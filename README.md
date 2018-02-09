# Docker for Android SDK 23

Docker for Android SDK 23 with preinstalled build tools and emulator image

> Edit from [mindrunner/docker-android-sdk](https://github.com/mindrunner/docker-android-sdk)

**Installed Packages**
```bash
# sdkmanager --list
  Path                                        | Version | Description                                | Location
  -------                                     | ------- | -------                                    | -------
  build-tools;27.0.3                          | 27.0.3  | Android SDK Build-Tools 27.0.3             | build-tools/27.0.3/
  emulator                                    | 27.1.7  | Android Emulator                           | emulator/
  patcher;v4                                  | 1       | SDK Patch Applier v4                       | patcher/v4/
  platform-tools                              | 27.0.1  | Android SDK Platform-Tools                 | platform-tools/
  platforms;android-23                        | 2       | Android SDK Platform 24                    | platforms/android-23/
  system-images;android-23;google_apis;x86_64 | 20      | Google APIs Intel x86 Atom_64 System Image | system-images/android-23/google_apis/x86_64/
  tools                                       | 26.1.1  | Android SDK Tools                          | tools/
```

**Usage**

- Interactive way
  ```bash
  $ docker run -it --rm --privileged androidsdk/android-23:latest bash
  # check installed packages
  $ sdkmanager --list
  # create and run emulator
  $ avdmanager create avd -n first_avd -k "system-images;android-23;google_apis;x86_64"
  $ emulator -avd first_avd -no-window -no-audio &
  $ adb devices
  # You can also run other Android platform tools, which are all added to the PATH environment variable
  ```

- Non-interactive way
  ```bash
  # check installed packages
  $ docker run -it --rm androidsdk/android-23:latest sdkmanager --list
  # create and run emulator
  $ docker run -it --rm androidsdk/android-23:latest avdmanager list avd
  # You can also run other Android platform tools, which are all added to the PATH environment variable
  ```