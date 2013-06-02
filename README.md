Device files for the Samsung Galaxy Player 5.0 USA

## Building ROMs

The files in this folder are the product of the aries-common folder from https://github.com/CyanogenMod/android_device_samsung_aries-common
and the vibrantmtd folder from https://github.com/CyanogenMod/android_device_samsung_vibrantmtd merged into one, and modified to run on the
US Samsung Galaxy Player 5.0 aka venturi_usa.

In order to build CM-10.1 for this device, sync the entire CyanogenMod repo (instsructions here: http://wiki.cyanogenmod.org/w/Build_for_vibrantmtd) but do up to where you run "repo sync" and it downloads the source. After the source is all downloaded, create a file under (source-tree-root)/.repo/local_manifests/roomservice.xml and copy the following into that and save:

```bash
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <project name="JackpotClavin/android_device_samsung_venturi_usa" path="device/samsung/venturi_usa" remote="github" revision="cm-10.1" />
  <project name="JackpotClavin/android_vendor_samsung_venturi_usa" path="vendor/samsung/venturi_usa" remote="github" revision="cm-10.1" />
  <project name="JackpotClavin/android_kernel_samsung_venturi" path="kernel/samsung/venturi" remote="github" revision="3.0Venturi" />
  <project name="CyanogenMod/android_hardware_samsung" path="hardware/samsung" remote="github" revision="cm-10.1" />
</manifest>
```

Then, run "repo sync" one more time. After it gets the device, vendor, kernel, and Samsung hardware files you will be able to build.

The after syncing the entire CyanogenMod source tree and the Venturi files, type:

```bash
. build/envsetup.sh
```
then type:

```bash
. vendor/cm/get-prebuilts 
```

and then the build command is:

```bash
brunch venturi_usa
```

Modification and improving the aforementioned source tree is strongly encouraged! Happy building!

## Building just the kernel and boot.img

A tip: If you're just making a kernel, you don't have to make an entire .zip file. Instead, type:

```bash
. build/envsetup.sh
```

Then, type:

```bash
lunch cm_venturi_usa-userdebug
```

And to direct your build environment to make just a bootimage, type:

```bash
mka bootimage
```

This will build the kernel and ramdisk and recovery and package it into a nice boot.img that you can install (should be around 5.6MB)
