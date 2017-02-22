# Retrofit2 入门教程一

>retrofit是现在Android开发者中最受欢迎的框架之一，squareup出品，retrofit功能十分强大。

- 配置 `build.gradle` 添加依赖 

```xml
compile 'com.squareup.retrofit2:retrofit:2.2.0'
```
- 配置 `AndroidManifest.xml` 添加网络访问权限

```xml
<uses-permission android:name="android.permission.INTERNET"/>
```

- 新建 `Service.java` 访问网络的接口应统一放在这个接口中

```java
package com.retrofit.baseHttp;

import retrofit2.Call;
import retrofit2.http.GET;
import retrofit2.http.Query;
//
public interface Service {
    @GET("/")
    Call<String> getBaidu(@Query("sort") String sort);
}


```