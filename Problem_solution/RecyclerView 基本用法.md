#RecyclerView 

##什么是RecyclerView？
> 不关心Item是否显示在正确的位置如何显示
> 不关心Item间如何分割
> 不关注Item增加与删除的动画效果
> 仅仅关注如何回收和复用View

##RecyclerView 相关的重要类
- Adapter
- ViewHolder
- Layoutmanager
- ItemDecoration
- ItemAnimator

##RecyclerView 能干什么
- List
- GridView
- 横向List
- 横向GridView
- 瀑布流
- 定制Item增加和删除动画

##如何使用

* app 目录下bulid.gradle添加
```xml
dependencies {
    ...
    compile 'com.android.support:recyclerview-v7:25.1.1'
}       
```
*  layout.xml添加

```xml
    <android.support.v7.widget.RecyclerView
         android:id="@+id/recycleListView"
         android:layout_width="match_parent"
         android:layout_height="match_parent">

     </android.support.v7.widget.RecyclerView>

```



