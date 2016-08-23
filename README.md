# Fix OpenGApps permissions on CyanogenMod 13

Updating to CyanogenMod 13 with OpenGApps is problematic and results in issues including repeated warnings such as 

> Unfortunately, setup wizard has stopped working

Or

> Unfortunately, Google Play Services has stopped working

Or the Setup Wizard asking you to set up your device but not allowing you to proceed.

----

The problem originates from Google Core apps not having required permissions and thus crashing or otherwise not working properly.
This fix grants the required permissions to Google Apps and was originally [written](https://github.com/TeamExodus/frameworks_base/commit/9c36be651e83fb039a262682839bd920b033007a) by @TheCrazyLex and consists of a ROM patch.
I converted it to a bash script that utilizes `pm grant` to achieve the same result without the requirement of patching your ROM.

## Usage

Place the script on your device and execute it *after CyanogenMod booted*, you may delete the file afterwards.

```shell
adb push fix_open_gapps_permissions.sh /sdcard/
adb shell 'bash /sdcard/fix_open_gapps_permissions.sh'
adb shell 'rm /sdcard/fix_open_gapps_permissions.sh'
```

If you don't have access to ADB, you can download the file onto your device or move it to sdcard. To execute it, enable *Developer Options → Local terminal* and use the `Terminal` app.