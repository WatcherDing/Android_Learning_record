#Android Activity 跳转动画设置 

###anim下创建动画文件

- slide_left_in.xml  (左边进入)
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <set xmlns:android="http://schemas.android.com/apk/res/android" >
    
        <translate
            android:duration="200"
            android:fromXDelta="-100.0%p"
            android:toXDelta="0.0" />
    
    </set>
    ```
- slide_left_out.xml  (左边退出)
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <set xmlns:android="http://schemas.android.com/apk/res/android" >
    
        <translate
            android:duration="200"
            android:fromXDelta="0.0"
            android:toXDelta="-100.0%p" />
    
    </set>
    ```    
- slide_right_in.xml  （右边进入）

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <set xmlns:android="http://schemas.android.com/apk/res/android" >
    
        <translate
            android:duration="200"
            android:fromXDelta="100.0%p"
            android:toXDelta="0.0" />
    
    </set>
    ```
- slide_right_out.xml  （右边退出）
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <set xmlns:android="http://schemas.android.com/apk/res/android" >
    
        <translate
            android:duration="200"
            android:fromXDelta="0"
            android:toXDelta="100.0%p" />
    
    </set>
    ```
###在style.xml设置
    ```xml
        <!--动画跳转-->
        <style name="Animation_Activity"
            parent="@android:style/Animation.Activity">
            <item name="android:activityOpenEnterAnimation">@anim/in_from_right</item>
            <item name="android:activityOpenExitAnimation">@anim/out_from_left</item>
            <item name="android:activityCloseEnterAnimation">@anim/in_from_left</item>
            <item name="android:activityCloseExitAnimation">@anim/out_from_right</item>
        </style>
    ```    
 |属性|作用|
 |----|----|
 |activityOpenEnterAnimation|一个activity创建进入的效果|   
 |activityOpenExitAnimation|activity还没有finish()下退出效果, 比如有俩个activity A与B 首先启动A 然后再启动B 那么A还没有finish()  这时A的退出效果。|   
 |activityCloseEnterAnimation|表示上一个activity返回进入效果 比如有俩个activity A与B  B在最上面，B退出(finish)后 A重新进入的效果|   
 |activityCloseExitAnimation|表示的是activity finish()之后的效果 比如有俩个activity A与B B退出后会被finish() 那么B的退出效果在这定义。|   
 
 
###使用方法一
- 第一步
```xml
    <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
        <item name="android:windowAnimationStyle">@style/Animation_Activity</item>
    </style>
```
- 第二步

    ```xml
    <application
        ......
        android:theme="@style/AppTheme">
    ```

```xml
       <!--设置activity属性 Theme -->
       <activity
        android:name=".View.xxxActivity"
        android:label="@string/xxxActivity"
        android:theme="@style/AppTheme" /> 
```





    
    
