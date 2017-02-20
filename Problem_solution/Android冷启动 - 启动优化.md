#android 启动优化，消除启动白屏，黑屏
###介绍：
    Android启动时候默认有短暂的白屏现象
###方法
* 在 `drawable` 下新建 `launch_screen.xml` 

```xml
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android"
    android:opacity="opaque">

    <item android:drawable="@android:color/white">
    </item>

    <item>
        <bitmap android:src="@mipmap/ic_launcher"
            android:gravity="center"
            />
    </item>
</layer-list>

```

* 在 `style.xml` 中添加一个新的主题

```xml
    <style name="AppTheme.Launcher">
        <item name="android:windowBackground">@drawable/launch_screen</item>
    </style>
```