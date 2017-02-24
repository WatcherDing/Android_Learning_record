# Retrofit2 入门教程三
>之前我们介绍了Retrofit 获取数据赋值给定义的对象List<T>，现在来学习添加到列表。本次使用的`recycleview`。之前一直在研究React native 很多Android的知识都忘掉了，甚至之前不曾知道recycleview这个控件。有什么讲错的欢迎指出。

- 添加 recycleview 万能适配器和处理图片依赖

```xml
    //万能适配器
    compile 'com.zhy:base-rvadapter:3.0.3'
    //glide 图片加载依赖
    compile 'jp.wasabeef:glide-transformations:2.0.1'
    //图片圆角等依赖
    compile 'com.github.bumptech.glide:glide:3.7.0'
    
```
 
- 新建`item.xml` item布局非常简单

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:orientation="horizontal" android:layout_width="match_parent"
    android:layout_height="wrap_content">

    <ImageView
        android:layout_width="100px"
        android:layout_height="100px"
        app:srcCompat="@mipmap/ic_launcher"
        android:id="@+id/imageView"
        />

    <TextView
        android:text="TextView"
        android:layout_width="wrap_content"
        android:gravity="center_vertical"
        android:layout_height="wrap_content"
        android:id="@+id/textView"
        android:layout_weight="1" />

</LinearLayout>

```

- 在 `onCreate` 方法调用`initView();`

```java
    private RecyclerView recycleview;
    public void initview(){
        recycleview = (RecyclerView) findViewById(R.id.recyclerView);
        recycleview.setLayoutManager(getLayoutManager());
    }
    public LinearLayoutManager getLayoutManager() {

        LinearLayoutManager mLayoutManager = new LinearLayoutManager(this) {
            //重写这个方法是为了防止在ScrollView下的recycleview滑动卡顿
            @Override
            public boolean canScrollVertically() {
                return false;
            }
        };
        mLayoutManager.setOrientation(OrientationHelper.VERTICAL);
        return mLayoutManager;
    }
```
