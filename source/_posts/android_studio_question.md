title: android studio（APP）常见问题与解决方法
date: 2016-01-15 13:51:52
categories: "APP"
tags: ["Android studio","APP","常见问题"]
---
主要内容：ADB,AVD's configuration,ANDROID_SDK_ROOT，架包问题
<!--more-->
1.android studio运行出现ADB not responding. If you'd like to retry, then please manually kill "adb.exe" and click 'Restart'
===========
解决方法一：
cmd下：
F:\Android\sdk\platform-tools>adb kill-server
F:\Android\sdk\platform-tools>adb start-server

解决方法二：
由于某些原因，ADB server的端口5037可能会被占用，
修改adb的端口号
设置环境变量ANDROID_ADB_SERVER_PORT=（你想要的值，如9999）
win下只要在环境变量中增加一个ANDROID_ADB_SERVER_PORT ，值填你自己定义的端口。


2.android studio运行出现This AVD's configuration is missing a kernel file,ANDROID_SDK_ROOT is undefined
=====================================
解决：这种错误一般由于Android studio的模拟器错误，将模拟器重新配置使之能够运行起来再利用它运行程序

3.Android studio找不到类actionbaractivity或者AppCompatActivity
====================
注意：actionbaractivity已经过时，现在一般选择AppCompatActivity
  解决：这是因为因为没有导入android-support-v7-appcompat包而导致我找不到相应的类，导入android-support-v7-appcompat.jar包就可以
	解压android-support-v7-appcompat.jar包可以查看是不是有对应的类，没有的话建议重新下载版本高一点的包
操作步骤：
	右键->open module settings弹出窗口，上面选择Dependencies
	点击加号"+",选择Library dependency
	选择appcompat-v7,点击ok

4.CPU acceleration status: HAXM must be updated (version 1.1.1 < 6.0.1).
==========
解决：打开SDK安装HAXM，打开D:\Android\sdk\extras\intel\Hardware_Accelerated_Execution_Manager，双击intelhaxm-android.exe 安装即可。




5.Error:Execution failed for task ':app:dexDebug'.com.android.ide.common.process.ProcessException: org.gradle.process.internal.ExecException: Process 'command 'D:\Java\jdk1.8.0_65\bin\java.exe'' finished with non-zero exit value 2
===========================
解决：
build.gradle文件中添加
defaultConfig {
    multiDexEnabled true
}

6.Error:failed to find Build Tools revision 24.0.0 rc3
-------------------
每个项目的build.gradle里可以设置，例如
```
android {
    ....
    buildToolsVersion '24.0.0 rc3'
    ....
}
```
如下图，我的Android SDK 没有安装Build-tools 24 rc3
![image](img/android_studio_question/1.png)
所以 ，在build.gradle里面改成如下：
```
android {
    ....
    buildToolsVersion '23.0.3'
    ....
}
```
再执行Tools–>Android–>Sync Project with Gradle Files即可 