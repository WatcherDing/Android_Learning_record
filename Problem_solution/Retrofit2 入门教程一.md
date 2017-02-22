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
import retrofit2.http.POST;
public interface Service {

    @GET("/")
    Call<String> getBaidu();
    
    @POST("/")
    Call<String> getGoogle();

}
```
上面代码只需要知道：

    - @GET 是GET请求
    - @POST 是POST请求
    其它不明白没有问题，知道这些就够了，详细介绍会在下篇文章做介绍

- `MainActivity.java` 添加代码

```java
@Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        //创建访问前的配置信息
        Retrofit retrofit = new Retrofit.Builder()
                //访问的url地址主目录
                .baseUrl("http://www.baidu.com")
                //转化器，这里是将访问返回的数据转化为String
                //可以根据自己的需求，转化成任意类型
                // 以后会介绍开源的转化库一行代码就解决
                // 但是依然要求我们需要知道有这么个方法
                .addConverterFactory(new Converter.Factory() {
                    @Override
                    public Converter<ResponseBody, ?> responseBodyConverter(Type type, Annotation[] annotations, Retrofit retrofit) {
                        return new Converter<ResponseBody, String>() {
                            @Override
                            public String convert(ResponseBody value) throws IOException {
                                return value.string();
                            }
                        };
                    }
                })
                .build();

        Call<String> call = retrofit.create(Service.class).getBaidu();
        //访问网络回调
        call.enqueue(new Callback<String>() {
            //访问成功
            @Override
            public void onResponse(Call<String> call, Response<String> response) {
               Log.e("请求成功，数据:", response.body());
            }

            //访问失败
            @Override
            public void onFailure(Call<String> call, Throwable t) {
                Log.e("请求失败","error");
            }
        });
    }
```
