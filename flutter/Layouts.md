如果从来没有接触过Layout布局使用，Flutter的UI Layouts学起来肯定还是有曲线的。



如果以前接触过类似的话，那其实还好。

比较困难的其实是：

> 我知道可能有这么一个东西，但是我不知道他具体是怎么存在的，以及可以支持什么。



Row & Column已经写过，写点别的。



- 当有需要指定padding、backgroundColor、width/height可以使用最简单的Container
- 当希望Row or Column的子Widget能撑满父元素的空间，那要用Expanded包一下
- 当希望两个组件可以互相叠放时-比如图片上放字-那就可以使用stack，里面要叠放的元素用Positioned包一下
- 还有其他更多复杂的组件，不知道用什么的时候，随缘吧