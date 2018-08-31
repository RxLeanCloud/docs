# Java SDK 安装和初始化
初始化的代码如下：

在云引擎等服务端运行环境下：

```java
LeanCloud.initialize("uay57kigwe0b6f5n0e1d4z4xhydsml3dor24bzwvzr57wdap","kfgz7jjfsk55r5a8a3y4ttd3je1ko11bkibcikonk32oozww");
LeanCloud.toggleLog(true);
RxLeanCloudJavaGeneral.link();
```

在 Android 环境下：

```java
LeanCloud.initialize("uay57kigwe0b6f5n0e1d4z4xhydsml3dor24bzwvzr57wdap","kfgz7jjfsk55r5a8a3y4ttd3je1ko11bkibcikonk32oozww");
LeanCloud.toggleLog(true);
RxLeanCloudJavaAndroid.link();
```