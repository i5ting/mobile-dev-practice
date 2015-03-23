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
- AsyncHttpClient(http://loopj.com/android-async-http/)
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

-----------


##活动的启动模式（4种）

- standard
- singleTop
- singleTask
- singleInstance

碎片

动态加载布局


## Android系统中GC什么情况下会出现内存泄露呢？

出现情况:
1. 数据库的cursor没有关闭
2.构造adapter时,没有使用缓存contentview
   衍生listview的优化问题-----减少创建view的对象,充分使用contentview,可以使用一静态类来优化处理getview的过程
3.Bitmap对象不使用时采用recycle()释放内存
4.activity中的对象的生命周期大于activity
调试方法: DDMS==> HEAPSZIE==>dataobject==>[Total Size]


## Dalvik基于JVM的改进

1. 几个class变为一个dex，constant pool，省内存
2. Zygote，copy-on-write shared,省内存，省cpu，省电
3. 基于寄存器的bytecode，省指令，省cpu，省电
4. Trace-based JIT,省cpu，省电,省内存


## 注册广播接收者两种方式的区别，及优缺点

答：首先写一个类要继承BroadcastReceiver
第一种:在清单文件中声明,添加
  
  <receiveandroid:name=".IncomingSMSReceiver " >
  <intent-filter>
     <actionandroid:name="android.provider.Telephony.SMS_RECEIVED")
  <intent-filter>
  <receiver>
    
第二种使用代码进行注册如:

  IntentFilterfilter =  newIntentFilter("android.provider.Telephony.SMS_RECEIVED");
  IncomingSMSReceiverreceiver = new IncomgSMSReceiver();
  registerReceiver(receiver.filter);
  
两种注册类型的区别是：

1)第一种是常驻型（静态注册），也就是说当应用程序关闭后，如果有信息广播来，程序也会被系统调用自动运行。
2)第二种不是常驻型广播（动态注册），也就是说广播跟随程序的生命周期。

注册的方法有两种，一种是静态注册，一种是动态注册。
动态注册优点：在 Android 的广播机制中，动态注册的优先级是要高于静态注册优先级的，因此在必要的情况下，我们是需要动态注册广播接收器的。

静态注册优点：动态注册广播接收器还有一个特点，就是当用来注册的 Activity 关掉后，广播也就失效了。同时反映了静态注册的一个优势，就是无需担忧广播接收器是否被关闭，只要设备是开启状态，广播接收器就是打开着的。



## android:gravity与android:layout_gravity的区别
LinearLayout有两个非常相似的属性：android:gravity与android:layout_gravity。他们的区别在 于：android:gravity用于设置View组件的对齐方式，而android:layout_gravity用于设置Container组件的 对齐方式。

举个例子，我们可以通过设置android:gravity="center"来让EditText中的文字在EditText组件中居中显示；同 时我们设置EditText的android:layout_gravity="right"来让EditText组件在LinearLayout中居右 显示。来实践以下：

正如我们所看到的，在EditText中，其中的文字已经居中显示了，而EditText组件自己也对齐到了LinearLayout的右侧

## AIDL的全称是什么?如何工作?能处理哪些类型的数据?

AIDL全称Android Interface Definition Language（Android接口描述语言）是一种借口描述语言; 编译器可以通过aidl文件生成一段代码，通过预先定义的接口达到两个进程内部通信进程跨界对象访问的目的.AIDL的IPC的机制和COM或CORBA类似, 是基于接口的，但它是轻量级的。它使用代理类在客户端和实现层间传递值. 如果要使用AIDL, 需要完成2件事情: 1. 引入AIDL的相关类.; 2. 调用aidl产生的class.理论上, 参数可以传递基本数据类型和String, 还有就是Bundle的派生类, 不过在Eclipse中,目前的ADT不支持Bundle做为参数,
具体实现步骤如下:

1、创建AIDL文件, 在这个文件里面定义接口, 该接口定义了可供客户端访问的方法和属性。

2、编译AIDL文件, 用Ant的话, 可能需要手动, 使用Eclipse plugin的话,可以根据adil文件自动生产java文件并编译, 不需要人为介入.

3、在Java文件中, 实现AIDL中定义的接口. 编译器会根据AIDL接口, 产生一个JAVA接口。这个接口有一个名为Stub的内部抽象类，它继承扩展了接口并实现了远程调用需要的几个方法。接下来就需要自己去实现自定义的几个接口了.
4、向客户端提供接口ITaskBinder, 如果写的是service，扩展该Service并重载onBind ()方法来返回一个实现上述接口的类的实例。
5、在服务器端回调客户端的函数. 前提是当客户端获取的IBinder接口的时候,要去注册回调函数, 只有这样, 服务器端才知道该调用那些函数

AIDL语法很简单,可以用来声明一个带一个或多个方法的接口，也可以传递参数和返回值。 由于远程调用的需要, 这些参数和返回值并不是任何类型.下面是些AIDL支持的数据类型:

1. 不需要import声明的简单Java编程语言类型(int,boolean等)

2. String, CharSequence不需要特殊声明

3. List, Map和Parcelables类型, 这些类型内所包含的数据成员也只能是简单数据类型, String等其他比支持的类型.

(另外: 我没尝试Parcelables, 在Eclipse+ADT下编译不过, 或许以后会有所支持).

实现接口时有几个原则:

.抛出的异常不要返回给调用者. 跨进程抛异常处理是不可取的.

.IPC调用是同步的。如果你知道一个IPC服务需要超过几毫秒的时间才能完成地话，你应该避免在Activity的主线程中调用。也就是IPC调用会挂起应用程序导致界面失去响应. 这种情况应该考虑单起一个线程来处理.

.不能在AIDL接口中声明静态属性。

IPC的调用步骤:

1. 声明一个接口类型的变量，该接口类型在.aidl文件中定义。

2. 实现ServiceConnection。

3. 调用ApplicationContext.bindService(),并在ServiceConnection实现中进行传递.

4. 在ServiceConnection.onServiceConnected()实现中，你会接收一个IBinder实例(被调用的Service). 调用

YourInterfaceName.Stub.asInterface((IBinder)service)将参数转换为YourInterface类型。

5. 调用接口中定义的方法。你总要检测到DeadObjectException异常，该异常在连接断开时被抛出。它只会被远程方法抛出。

6. 断开连接，调用接口实例中的ApplicationContext.unbindService()
参考：http://buaadallas.blog.51cto.com/399160/372090

## 根据自己的理解描述下Android数字签名。

(1)所有的应用程序都必须有数字证书，Android系统不会安装一个没有数字证书的应用程序
(2)Android程序包使用的数字证书可以是自签名的，不需要一个权威的数字证书机构签名认证
(3)如果要正式发布一个Android程序，必须使用一个合适的私钥生成的数字证书来给程序签名，而不能使用adt插件或者ant工具生成的调试证书来发布。
(4)数字证书都是有有效期的，Android只是在应用程序安装的时候才会检查证书的有效期。如果程序已经安装在系统中，即使证书过期也不会影响程序的正常功能。


## Manifest.xml文件中主要包括哪些信息？

manifest：根节点，描述了package中所有的内容。
uses-permission：请求你的package正常运作所需赋予的安全许可。
permission： 声明了安全许可来限制哪些程序能你package中的组件和功能。
instrumentation：声明了用来测试此package或其他package指令组件的代码。
application：包含package中application级别组件声明的根节点。
activity：Activity是用来与用户交互的主要工具。
receiver：IntentReceiver能使的application获得数据的改变或者发生的操作，即使它当前不在运行。
service：Service是能在后台运行任意时间的组件。
provider：ContentProvider是用来管理持久化数据并发布给其他应用程序使用的组件。

## View, surfaceView, GLSurfaceView有什么区别

view是最基础的，必须在UI主线程内更新画面，速度较慢。
SurfaceView 是view的子类，类似使用双缓机制，在新的线程中更新画面所以刷新界面速度比view快
GLSurfaceView 是SurfaceView的子类，opengl 专用的

## Android中Activity, Intent, Content Provider, Service各有什么区别。
Activity： 活动，是最基本的android应用程序组件。一个活动就是一个用户可以操作的可视化用户界面，每一个活动都被实现为一个独立的类，并且从活动基类继承而来。
Intent： 意图，描述应用想干什么。最重要的部分是动作和动作对应的数据。
Content Provider：内容提供器，android应用程序能够将它们的数据保存到文件、SQLite数据库中，甚至是任何有效的设备中。当你想将你的应用数据和其他应用共享时，内容提供器就可以发挥作用了。
Service：服务，具有一段较长生命周期且没有用户界面的程序组件。

## 谈谈android数据存储方式

Android提供了5种方式存储数据：
（1）使用SharedPreferences存储数据；它是Android提供的用来存储一些简单配置信息的一种机制，采用了XML格式将数据存储到设备中。只能在同一个包内使用，不能在不同的包之间使用。
（2）文件存储数据；文件存储方式是一种较常用的方法，在Android中读取/写入文件的方法，与Java中实现I/O的程序是完全一样的，提供了openFileInput()和openFileOutput()方法来读取设备上的文件。
（3）SQLite数据库存储数据；SQLite是Android所带的一个标准的数据库，它支持SQL语句，它是一个轻量级的嵌入式数据库。
（4）使用ContentProvider存储数据；主要用于应用程序之间进行数据交换，从而能够让其他的应用保存或读取此Content Provider的各种数据类型。
（5）网络存储数据；通过网络上提供给我们的存储空间来上传(存储)和下载(获取)我们存储在网络空间中的数据信息。

## 请解释下在单线程模型中Message、Handler、Message Queue、Looper之间的关系。

答：简单的说，Handler获取当前线程中的looper对象，looper用来从存放Message的MessageQueue中取出Message，再有Handler进行Message的分发和处理.
Message Queue(消息队列)：用来存放通过Handler发布的消息，通常附属于某一个创建它的线程，可以通过Looper.myQueue()得到当前线程的消息队列
Handler：可以发布或者处理一个消息或者操作一个Runnable，通过Handler发布消息，消息将只会发送到与它关联的消息队列，然也只能处理该消息队列中的消息
Looper：是Handler和消息队列之间通讯桥梁，程序组件首先通过Handler把消息传递给Looper，Looper把消息放入队列。Looper也把消息队列里的消息广播给所有的
Handler：Handler接受到消息后调用handleMessage进行处理
Message：消息的类型，在Handler类中的handleMessage方法中得到单个的消息进行处理
在单线程模型下，为了线程通信问题，Android设计了一个Message Queue(消息队列)， 线程间可以通过该Message Queue并结合Handler和Looper组件进行信息交换。下面将对它们进行分别介绍：
1. Message
    Message消息，理解为线程间交流的信息，处理数据后台线程需要更新UI，则发送Message内含一些数据给UI线程。
2. Handler
    Handler处理者，是Message的主要处理者，负责Message的发送，Message内容的执行处理。后台线程就是通过传进来的 Handler对象引用来sendMessage(Message)。而使用Handler，需要implement 该类的 handleMessage(Message)方法，它是处理这些Message的操作内容，例如Update UI。通常需要子类化Handler来实现handleMessage方法。
3. Message Queue
    Message Queue消息队列，用来存放通过Handler发布的消息，按照先进先出执行。
    每个message queue都会有一个对应的Handler。Handler会向messagequeue通过两种方法发送消息：sendMessage或post。这两种消息都会插在message queue队尾并按先进先出执行。但通过这两种方法发送的消息执行的方式略有不同：通过sendMessage发送的是一个message对象,会被 Handler的handleMessage()函数处理；而通过post方法发送的是一个runnable对象，则会自己执行。
4. Looper
    Looper是每条线程里的Message Queue的管家。Android没有Global的MessageQueue，而Android会自动替主线程(UI线程)建立Message Queue，但在子线程里并没有建立Message Queue。所以调用Looper.getMainLooper()得到的主线程的Looper不为NULL，但调用Looper.myLooper()得到当前线程的Looper就有可能为NULL。对于子线程使用Looper，API Doc提供了正确的使用方法：这个Message机制的大概流程：
    1. 在Looper.loop()方法运行开始后，循环地按照接收顺序取出Message Queue里面的非NULL的Message。
    2. 一开始Message Queue里面的Message都是NULL的。当Handler.sendMessage(Message)到Message Queue，该函数里面设置了那个Message对象的target属性是当前的Handler对象。随后Looper取出了那个Message，则调用 该Message的target指向的Hander的dispatchMessage函数对Message进行处理。在dispatchMessage方法里，如何处理Message则由用户指定，三个判断，优先级从高到低：
    1) Message里面的Callback，一个实现了Runnable接口的对象，其中run函数做处理工作；
    2) Handler里面的mCallback指向的一个实现了Callback接口的对象，由其handleMessage进行处理；
    3) 处理消息Handler对象对应的类继承并实现了其中handleMessage函数，通过这个实现的handleMessage函数处理消息。
    由此可见，我们实现的handleMessage方法是优先级最低的！
    3. Handler处理完该Message (updateUI) 后，Looper则设置该Message为NULL，以便回收！
    在网上有很多文章讲述主线程和其他子线程如何交互，传送信息，最终谁来执行处理信息之类的，个人理解是最简单的方法——判断Handler对象里面的Looper对象是属于哪条线程的，则由该线程来执行！
    1. 当Handler对象的构造函数的参数为空，则为当前所在线程的Looper；
    2. Looper.getMainLooper()得到的是主线程的Looper对象，Looper.myLooper()得到的是当前线程的Looper对象。


## 如何退出Activity

对于单一Activity的应用来说，退出很简单，直接finish()即可。当然，也可以用killProcess()和System.exit()这样的方法。现提供几个方法，供参考：
1、抛异常强制退出：该方法通过抛异常，使程序Force Close。验证可以，但是，需要解决的问题是，如何使程序结束掉，而不弹出Force Close的窗口。
2、记录打开的Activity：每打开一个Activity，就记录下来。在需要退出时，关闭每一个Activity即可。
3、发送特定广播：在需要结束应用时，发送一个特定的广播，每个Activity收到广播后，关闭即可。
4、递归退出在打开新的Activity时使用startActivityForResult，然后自己加标志，在onActivityResult中处理，递归关闭。除了第一个，都是想办法把每一个Activity都结束掉，间接达到目的。但是这样做同样不完美。你会发现，如果自己的应用程序对每一个Activity都设置了nosensor，在两个Activity结束的间隙，sensor可能有效了。但至少，我们的目的达到了，而且没有影响用户使用。为了编程方便，最好定义一个Activity基类，处理这些共通问题。


http://blog.csdn.net/superjunjin/article/category/1192401

