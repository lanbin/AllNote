半夜睡不着，摸手机看今日头条扫到Flutter开发者大会的直播。
当时全程吐槽之后，第二天起来开始认真了解Flutter。

- 科学上网的东西就不细说了
- 其他的东西，想到了再提

## 环境配置
在Mac上使用`flutter doctor`进行工具配置还是比较简单的
```
[✓] Flutter (Channel stable, v1.0.0, on Mac OS X 10.14.1 18B75, locale
    zh-Hans-CN)
   这个成功，需要官网下载Flutter的包，解压放置在用户根目录，然后修改配置文件。
   按照官网的说明来

[✓] Android toolchain - develop for Android devices (Android SDK 28.0.3)
   这个成功，下载安卓相关的SDK

[✓] iOS toolchain - develop for iOS devices (Xcode 10.1)
   这个成功，下载安装Xcode, 根据提示来进行配置。
   还会要通过brew安装一些工具，
   比较坑的是`cocoapods`，建议去github上直接download他整个包，大概将近300M。用`git clone`会很慢很慢的。然后丢在`~/.cocoapods/repos/master/`下

[✓] Android Studio (version 3.1)
    这个成功，就安装吧。

[✓] VS Code (version 1.29.1)
    这个成功，就安装吧。新版本的VS Code速度快了很多。而且针对Flutter的插件还是比较好用的。

[✓] Connected device (1 available) 
    连上启用USB调试的手机或者启动Simulator都可以。
```

## 创建项目

打开VS  Code，把插件一通安装完#8，command + shift + p就可以看到命令板里面有：

 > flutter: new project

或者在命令行里面cd到自己的文件夹中：

> flutter create .

## 预览项目

找到Debug面板， 点绿色的小箭头就可以了。

**第一次运行，Flutter需要去下载一些依赖。这些依赖呢，就需要科学上网。**
**网上有可以把依赖配置改成国内的镜像，但是并不好用。所以最好还是通过科学上网大概等待几分钟就可以了。SS调到PAC自动模式就可以。**

下载完之后，后面进行开发调试就都很快了，毕竟有热替换。

## iOS Simulator

在使用iOS模拟器的时候因为之前手动把Simulator的缓存文件删掉了
导致在选择设备的时候提示`设备不存在`之类的。
使用`xcrun simctl erase all`完美解决问题，来自Stack Overflow的解决方案。

以上，就基本可以开始跟着官网的教程走了。
