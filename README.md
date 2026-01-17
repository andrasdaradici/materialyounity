# MaterialYounity - Themed icons made easy

MaterialYounity is an Android plugin created for Unity which allows you to take advantage of the "Material You" themed icons feature of Android with ease. The following guide will help you get started with using this small plugin.

<img width="4800" height="2670" alt="SampleImageMaterialYounity" src="https://github.com/user-attachments/assets/65c97161-4914-49d2-8842-896b32fc55ab" />

## Prerequisites

- **Unity** (latest version recommended, for this guide I used 6000.3.0b4)
- **Android Studio** (for building the .AAR)
- Basic knowledge of **Unity** and **Android development**

## Setup Guide

### 1. Prepare Assets

Before you begin, make sure you have the necessary assets for your app's icons:

- `ic_launcher_background.png` (Colored background image)
- `ic_launcher_foreground.png` (Colored foreground image)
  - ~~Small notice: No idea why the foreground icon decided to not render so (as you can see in the example icons) I have merged the foreground element into the background image and it renders well that way. I've got no idea at all why this happens.~
  - The issue was that I was an idiot and named the foreground to background and vice-versa, all is good.
- `ic_launcher_monochrome.png` (White icon on transparent background)

Ensure these images are sized appropriately (e.g., 432x432 px for the icon) and follow the Material You icon design standards.

### 2. Android Studio Part

1. **Clone or Download** the MaterialYounity repository from GitHub.
2. Open the project in **Android Studio**.
3. Replace the placeholder icons (`ic_launcher_background.png`, `ic_launcher_foreground.png`, `ic_launcher_monochrome.png`) with your own assets in the `app/src/res/drawable` folder.
4. In Android Studio, **Build -> Assemble Selected Modules** to generate the `.aar` (Android Archive) file.

### 3. Dropping the AAR into Unity

1. Copy the generated `.aar` file to your Unity project's `Assets/Plugins/Android` directory. (Found in `app/build/outputs/aar/` named `app-debug.aar`, you may rename it to anything.)
2. Make sure Unity detects the `.aar` file as a plugin.
3. If Unity doesn't automatically import the plugin, right-click the `.aar` file and select **Reimport**.

### 4. Custom Main and Launcher Manifest

Modify your **Main** and **Launcher** manifests to work with the MaterialYounity plugin.

#### Main Manifest (AndroidManifest.xml)
In your **AndroidManifest.xml** file, add the following:
```xml
<application
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name">
    <!-- Other configurations and permissions -->
</application>
```

#### Launcher Manifest (LauncherManifest.xml)

In your LauncherManifest.xml file, add the following:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:tools="http://schemas.android.com/tools"
          android:installLocation="preferExternal">
    <supports-screens
        android:smallScreens="true"
        android:normalScreens="true"
        android:largeScreens="true"
        android:xlargeScreens="true"
        android:anyDensity="true"/>

    <application
        android:label="@string/app_name"
        android:icon="@mipmap/app_icon">
    </application>
</manifest>
```
