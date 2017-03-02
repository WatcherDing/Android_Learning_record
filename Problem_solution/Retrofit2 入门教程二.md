# Retrofit2 入门教程二

>这次我们使用 Retrofit2 访问这个链接地址 [http://www.tngou.net/api/food/list?id=3&rows=10](http://www.tngou.net/api/food/list?id=3&rows=10)

- 这次请求的样式
```java
{
    status: true,
    total: 5,
    tngou: [
        {
            count: 672,
            description: "其他说明党参原产于山西上党，所以称为党参，功效与人参类似，只是效力不如人参强，同样也是实症、热症的人不能用",
            disease: "",
            fcount: 0,
            food: "",
            id: 189,
            img: "/food/150804/5c7e50b6fcb9ab950f7c23c75ca3b19d.jpg",
            keywords: "党参 人参 功效 经常出现 排骨汤 ",
            name: "党参",
            rcount: 0,
            summary: "",
            symptom: ""
        },
        {.....}
    ]
}
```

- 添加接口 

```java

public interface Service {
    @GET("/api/food/list")
    Call<String> getFood(@Query("id")int id,@Query("rows")int rows);
}

```
- 访问接口
```java
void getFood() {
        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("http://www.tngou.net")
                .addConverterFactory(new Converter.Factory() {
                    @Override
                    public Converter<ResponseBody, String> responseBodyConverter(
                            Type type,
                            Annotation[] annotations,
                            Retrofit retrofit) {
                        return new Converter<ResponseBody, String>() {
                            @Override
                            public String convert(ResponseBody value) throws IOException {
                                return value.string();
                            }
                        };
                    }
                }).build();
        Call<String> call = retrofit.create(Service.class).getFood(3,10);

        call.enqueue(new Callback<String>() {
            @Override
            public void onResponse(Call<String> call, Response<String> response) {
                Log.e("请求成功，数据:", response.body());
            }
            //访问失败的回调用
            @Override
            public void onFailure(Call<String> call, Throwable t) {
                Log.e("请求失败", "error");
            }
        });
    }
```
- 运行就能看到输出的数据：![](/assets/20170223205459.png)
- 现在上面估计你已经明白链接是怎么组成的，在接口中声明的
`@GET("/api/food/list")` 会添加在`Retrofit`的`baseUrl` 之后。参数在`Call<String> call = retrofit.create(Service.class).getFood(3,10);` getFood是接口的名字，3对应id，10对应rows会追加到`http://www.tngou.net/api/food/list
 `之后，组成 `http://www.tngou.net/api/food/list?id=3&rows=10`
### json数据解析
- 服务器返回的数据是json类型，现在获取到的是`String`难道需要我们在 请求成功回调后的方法中手动转化吗？不是的。`squareup` 提供了转化的工具包`converter-gson`,添加依赖
```xml
 compile 'com.squareup.retrofit2:converter-gson:2.2.0'
```
- 首先我们需要创建一个`Food.java`,（推荐使用GsonFormat插件创建）

```java
import com.google.gson.annotations.SerializedName;

import java.util.List;

public class FoodList {
    @SerializedName("status")
    private boolean status;
    @SerializedName("total")
    private int total;
    @SerializedName("tngou")
    private List<TngouBean> tngou;

    public static class TngouBean {
        @SerializedName("count")
        private int count;
        @SerializedName("description")
        private String description;
        @SerializedName("disease")
        private String disease;
        @SerializedName("fcount")
        private int fcount;
        @SerializedName("food")
        private String food;
        @SerializedName("id")
        private int id;
        @SerializedName("img")
        private String img;
        @SerializedName("keywords")
        private String keywords;
        @SerializedName("name")
        private String name;
        @SerializedName("rcount")
        private int rcount;
        @SerializedName("summary")
        private String summary;
        @SerializedName("symptom")
        private String symptom;
        
        //get set 方法
        //...
    }
    //get set 方法
    //...
}

```
- 修改接口的泛型为我们创建的FoodList类型
```java
public interface Service {
    //修改接口的泛型为我们创建的FoodList类型
    @GET("/api/food/list")
    Call<FoodList> getFood(@Query("id")int id, @Query("rows")int rows);
}
```
- 修改

```java
     void getFood() {
        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl("http://www.tngou.net")
                .addConverterFactory(GsonConverterFactory.create())
                .build();
        Call<FoodList> call = retrofit.create(Service.class).getFood(3,10);
        call.enqueue(new Callback<FoodList>() {
            @Override
            public void onResponse(Call<FoodList> call, Response<FoodList> response) {
                FoodList list=  response.body();
            }
            //访问失败的回调用
            @Override
            public void onFailure(Call<FoodList> call, Throwable t) {
                Log.e("请求失败", "error");
            }
        });
    }


```

- 运行后就看到![](/assets/20170223212856.png)
