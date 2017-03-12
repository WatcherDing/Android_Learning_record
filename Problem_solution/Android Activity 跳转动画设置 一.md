#Android Activity 跳转动画设置 

###创建动画文件

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
    
    
    
    
