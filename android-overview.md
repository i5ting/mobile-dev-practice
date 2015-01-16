# android-overview

# 基础

- java基础
- dalvik编译，以及zypote受精卵

### 下载

- SDK
- NDK（for c/c++）

### IDE

- adt
- Android Studio（荐）

构建

- adt使用ant/mvn构建
- Android Studio使用gradle

### Tools

- adb

# 3大部分
## 1. 组件ASBC

### A

- activity
	- activity/fragment
	- db/sp等单位
	- 动画
	- 自定义控件
	- 2d/3d
	- 传感器
	- webview
	- 短信等
	- 多媒体
- application

### S

- service

### B

- broadcastReceiver

有3种场景

- 1：n
- 接力
- 本地

另外需要比较广播VS通知VS推送

通知是Notification

### C

- content provider

跨应用共享数据

## 2. Manifest 应用程序清单

## 3. 资源

- resources
- assets


# 总结归类

## 万事万物皆意图

intent 就是传输队长，传输消息和数据

- 显式
- 隐式
- activity
- broadcast
- content provider
- 多媒体
- service

## Cache

- 文件读写io
- SharedPreffences键值对
- db（默认是sqlite）
	- sqlite
	- greendao
- content provider

## 多线程

- Thread类和runnable接口
- AsyncTast（底层是ExecutorService）
- Handler

## HTTP

- HttpUrlConnection
- HttpClient
- Volley（新，荐，未来可能标准）

## IPC

- Binder
- ADIL


## 消息相关

- 广播
- 通知 
- 推送
- 观察者模式

## 测试

- JUnit
- TestNG

测试工具

- Monkey/MonkeyRunner


## 其他

- 推送
- 上线
- scala(scala-lang.org) && sbt(https://github.com/sbt/sbt)
- jni/c/other语言：lua，mruby等
- 内购
- 地图


# Best Practice

- gradle构建
- jenkins做CI
- github托管代码仓库
- Gerrit代码审查
- mam（自己写的应用商店）

