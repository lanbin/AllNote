忽略了ListView的重要性。

之前在Row&Column里面聊到的说可以分割屏幕。

其实Row&Column更多的应该是分割自己的父元素的空间，并且提供一些快捷的布局方案。

如果一个页面是要一直滚动的话，其实还是需要ListView来进行整体的排版的。因为只有他才可以滚动，滚动啊。



比如，知乎日报这样的APP。

```dart
ListView(
  <Widget>[
    SizedBox(
      Swiper,
    ),
    Text('今日热文'),
    // 嵌套的ListView，需要设置这两个值才可以跟着整个页面滚动
    // 而不是页面滚完了，它在自己的区域滚动
    ListView(
      // 很重要的东西啊，ListView嵌套ListView
      shrinkWrap: true,
      // 这个是禁止了物理的滚动事件，导致自己不滚和大页面滚。
      physics: ClampingScrollPhysics(),
    ),
  ]
)
```

