# Android style 常用属性
- 4.4之后设置状态栏颜色

    ```xml
    <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
    ```
- 设置是否全屏显示

    ```xml
     <item name="android:windowFullscreen">false</item>
    ```
- 设置窗体的颜色

    ```xml
    <item name="windowBackground">@color/colorxx</item>
    ```
- 设置状态栏透明

    ```xml
    <item name="android:windowTranslucentStatus">true</item>
    ```
- Android 自带的主题样式
    ```java
         android:theme="@android:style/Theme.Dialog" // 将一个Activity显示为对话框模式
         android:theme="@android:style/Theme.NoTitleBar" // 不显示应用程序标题栏
         android:theme="@android:style/Theme.NoTitleBar.Fullscreen" // 不显示应用程序标题栏，并全屏
         android:theme="@android:style/Theme.Light" // 背景为白色
         android:theme="@android:style/Theme.Light.NoTitleBar" // 白色背景并无标题栏
         android:theme="@android:style/Theme.Light.NoTitleBar.Fullscreen" // 白色背景，无标题栏，全屏
         android:theme="@android:style/Theme.Black" // 背景黑色
         android:theme="@android:style/Theme.Black.NoTitleBar" // 黑色背景并无标题栏
         android:theme="@android:style/Theme.Black.NoTitleBar.Fullscreen" // 黑色背景，无标题栏，全屏
         android:theme="@android:style/Theme.Wallpaper" // 用系统桌面为应用程序背景
         android:theme="@android:style/Theme.Wallpaper.NoTitleBar" // 用系统桌面为应用程序背景，且无标题栏
         android:theme="@android:style/Theme.Wallpaper.NoTitleBar.Fullscreen" // 用系统桌面为应用程序背景，无标题栏，全屏
         android:theme="@android:style/Translucent" // 半透明效果
         android:theme="@android:style/Theme.Translucent.NoTitleBar" // 半透明并无标题栏
         android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" // 半透明效果，无标题栏，全屏
    ```
- Android 字体大小
    ```java
    "?android:attr/textAppearanceLarge"
     "?android:attr/textAppearanceMedium"
     "?android:attr/textAppearanceSmall"
    ```
- Android 字体颜色
    ```java
     android:textColor="?android:attr/textColorPrimary"
     android:textColor="?android:attr/textColorSecondary"
     android:textColor="?android:attr/textColorTertiary"
     android:textColor="?android:attr/textColorPrimaryInverse"
     android:textColor="?android:attr/textColorSecondaryInverse"
    ```
    
    
    ![](/assets/20160329134244193.png)