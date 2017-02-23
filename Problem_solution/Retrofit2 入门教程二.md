# Retrofit2 入门教程一

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

- 添加依赖 `build.gradle` 帮助我们解析json数据的工具
```
    compile 'com.squareup.retrofit2:converter-gson:2.2.0'
```




