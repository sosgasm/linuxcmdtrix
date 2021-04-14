# Removing unwanted APK's from android device
The steps taken worked for my unbranded Android tablet. You can use it to remove bloatware/apps you don't use.
My goal was to remove the default browser and a google search bar.

#### Prerequisites
##### Install Fastboot + ADB (You only need ADB to remove bloatware, but Fastboot comes handy when modifying android devices)<br>


```
* $ sudo apt install libarchive-tools
* $ curl -O https://dl.google.com/android/repository/platform-tools_r31.0.1-linux.zip
* $ echo 'e347361d1e6f8802da64272903b07180199e75f1a3b6636f851744d32b2fb090  platform-tools_r31.0.1-linux.zip' | sha256sum
* $ unzip platform-tools**.zip
* $ export PATH="$PWD/platform-tools:$PATH"
* $ sudo apt install android-tools-adb
```

---

#### Get your device ready

```
* First, turn on your device and enable "Developer mode", look for "Settings" --> "Build number" --> Tap 6 times on build number until you get 
  message "you are now a developer"
* Enable "USB debugging": "Settings" --> "Enable Debugging"
* connect your tablet to your Linux tablet/pc (I'm Running Linux Mint atm"
* Let your tablet accept your computer's ADB RSA key print
```

### The commands

```
$ adb devices

You should get your device it's properties
```

```
Enable ADB Shell:

$ adb shell
```

```
List installed packages:

$ pm list packages -s
```

```
Remove a package but keep the apps data:

$ pm uninstall -k --user 0 <packagename>

OR

Remove a package and data

$ pm uninstall --user 0 <package name>
```

```
I removed my packages (default browser/google search bar on home screen (which was not a widget) using the following commands:

H8005:/ $ pm list packages -s | grep browser
package:com.android.browser
H8005:/ $ pm uninstall --user 0 com.android.browser
Success
```

```
Fin
```