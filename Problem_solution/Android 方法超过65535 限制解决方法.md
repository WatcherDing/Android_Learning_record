#Android 方法超过65535 限制解决方法

### 随着项目用到越来越多的jar，或者moudle ，相信很多人在编译过程中都会遇到下面这样的错误。

```java
UNEXPECTED TOP-LEVEL EXCEPTION:  
java.lang.IllegalArgumentException: method ID not in [0, 0xffff]: 65536  
```
- 上面的意思是说dex 中的方法超过了最大限制65535 

### 解决方法
- 第一步
```
defaultConfig {
        ...
        multiDexEnabled true
    }
dependencies {
    ...
    //方法超过65536
    compile 'com.android.support:multidex:1.0.1'
    }
```

- 第二步

```java
public class App extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MultiDex.install(this); 
    }
}
```

