# Android

android编程，2本书足矣：第一行代码 + 编程实战。

- 第一行代码：深入浅出，适合新人
- 编程实战：有深度，有难度，而且内容全面，较新，使用android studio

## 准备

下载android studio

## 配置环境变量


```
export JAVA_HOME=/System/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home
export PATH=$PATH:$JAVA_HOME/bin
export classpath=.:$JAVA_HOME/lib


export GROOVY_HOME=/Users/sang/bin/groovy-2.4.0-rc-2
export PATH=$PATH:$GROOVY_HOME/bin

export GRADLE_HOME=/Users/sang/bin/gradle-2.2.1
export PATH=$PATH:$GRADLE_HOME/bin


export ANDROID_SDK_HOME=/Users/sang/Library/Android/sdk

export ANDROID_NDK_HOME=/Users/sang/bin/android-ndk-r10d

export PATH=$PATH:$ANDROID_SDK_HOME/tools
export PATH=$PATH:$ANDROID_SDK_HOME/platform-tools
export PATH=$PATH:$ANDROID_SDK_HOME/build-tools/21.1.2
export PATH=$PATH:$ANDROID_NDK_HOME
```

### 安装Gradle


	Mac上会默认下载到 /Users/<用户名>/.gradle/wrapper/dists 目录
	Win平台会默认下载到 C:\Documents and Settings\<用户名>.gradle\wrapper\dists 目录
	
你会看到这个目录下有个 gradle-x.xx-all 的文件夹, 如果下载实在太慢，但是又不想翻墙的话，可以自己手动到Gradle官网下载对应的版本，然后将下载的.zip文件(也可以解压)复制到上述的gradle-x.xx-all 文件夹下，不过还是建议让它直接下载的好。

如果不这么处理，会报错哦，主要是gradle-wrapper.propertie

```
mkdir -p ~/.gradle/wrapper/dists
cp -rf $GRADLE_HOME/* ~/.gradle/wrapper/dists
```

臆测，需测试。


```
./gradlew --help
```

如果没有安装过gradle，他就会下载的


```
➜  IntentDemo git:(master) ✗ ./gradlew --help
Downloading https://services.gradle.org/distributions/gradle-2.2.1-all.zip
..................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Unzipping /Users/sang/.gradle/wrapper/dists/gradle-2.2.1-all/6dibv5rcnnqlfbq9klf8imrndn/gradle-2.2.1-all.zip to /Users/sang/.gradle/wrapper/dists/gradle-2.2.1-all/6dibv5rcnnqlfbq9klf8imrndn
Set executable permissions for: /Users/sang/.gradle/wrapper/dists/gradle-2.2.1-all/6dibv5rcnnqlfbq9klf8imrndn/gradle-2.2.1/bin/gradle

USAGE: gradlew [option...] [task...]

-?, -h, --help          Shows this help message.
-a, --no-rebuild        Do not rebuild project dependencies.
-b, --build-file        Specifies the build file.
-c, --settings-file     Specifies the settings file.
--configure-on-demand   Only relevant projects are configured in this build run. This means faster build for large multi-project builds. [incubating]
--continue              Continues task execution after a task failure.
-D, --system-prop       Set system property of the JVM (e.g. -Dmyprop=myvalue).
-d, --debug             Log in debug mode (includes normal stacktrace).
--daemon                Uses the Gradle daemon to run the build. Starts the daemon if not running.
--foreground            Starts the Gradle daemon in the foreground. [incubating]
-g, --gradle-user-home  Specifies the gradle user home directory.
--gui                   Launches the Gradle GUI.
-I, --init-script       Specifies an initialization script.
-i, --info              Set log level to info.
-m, --dry-run           Runs the builds with all task actions disabled.
--no-color              Do not use color in the console output.
--no-daemon             Do not use the Gradle daemon to run the build.
--offline               The build should operate without accessing network resources.
-P, --project-prop      Set project property for the build script (e.g. -Pmyprop=myvalue).
-p, --project-dir       Specifies the start directory for Gradle. Defaults to current directory.
--parallel              Build projects in parallel. Gradle will attempt to determine the optimal number of executor threads to use. [incubating]
--parallel-threads      Build projects in parallel, using the specified number of executor threads. [incubating]
--profile               Profiles build execution time and generates a report in the <build_dir>/reports/profile directory.
--project-cache-dir     Specifies the project-specific cache directory. Defaults to .gradle in the root project directory.
-q, --quiet             Log errors only.
--recompile-scripts     Force build script recompiling.
--refresh-dependencies  Refresh the state of dependencies.
--rerun-tasks           Ignore previously cached task results.
-S, --full-stacktrace   Print out the full (very verbose) stacktrace for all exceptions.
-s, --stacktrace        Print out the stacktrace for all exceptions.
--stop                  Stops the Gradle daemon if it is running.
-u, --no-search-upward  Don't search in parent folders for a settings.gradle file.
-v, --version           Print version info.
-x, --exclude-task      Specify a task to be excluded from execution.

➜  IntentDemo git:(master) ./gradlew tasks
> Configuring > 0/2 projects > root project
Download https://jcenter.bintray.com/com/android/tools/build/builder/1.0.0/builder-1.0.0.jar
Download https://jcenter.bintray.com/com/android/tools/lint/lint/24.0.0/lint-24.0.0.jar
Download https://jcenter.bintray.com/net/sf/proguard/proguard-gradle/5.1/proguard-gradle-5.1.jar
Download https://jcenter.bintray.com/com/android/tools/sdk-common/24.0.0/sdk-common-24.0.0.jar
Download https://jcenter.bintray.com/org/bouncycastle/bcprov-jdk15on/1.48/bcprov-jdk15on-1.48.jar
> Configuring > 0/2 projects > root project > 2.06 MB/2.21 MB downloaded
Download https://jcenter.bintray.com/com/squareup/javawriter/2.5.0/javawriter-2.5.0.jar
Download https://jcenter.bintray.com/com/android/tools/common/24.0.0/common-24.0.0.jar
Download https://jcenter.bintray.com/com/android/tools/build/builder-test-api/1.0.0/builder-test-api-1.0.0.jar
Download https://jcenter.bintray.com/com/android/tools/ddms/ddmlib/24.0.0/ddmlib-24.0.0.jar
Download https://jcenter.bintray.com/com/android/tools/build/manifest-merger/24.0.0/manifest-merger-24.0.0.jar
Download https://jcenter.bintray.com/com/android/tools/build/builder-model/1.0.0/builder-model-1.0.0.jar
Download https://jcenter.bintray.com/com/android/tools/sdklib/24.0.0/sdklib-24.0.0.jar
Download https://jcenter.bintray.com/org/bouncycastle/bcpkix-jdk15on/1.48/bcpkix-jdk15on-1.48.jar
Download https://jcenter.bintray.com/com/android/tools/lint/lint-checks/24.0.0/lint-checks-24.0.0.jar
Download https://jcenter.bintray.com/org/eclipse/jdt/core/compiler/ecj/4.2.2/ecj-4.2.2.jar
Download https://jcenter.bintray.com/net/sf/proguard/proguard-base/5.1/proguard-base-5.1.jar
Download https://jcenter.bintray.com/com/google/guava/guava/17.0/guava-17.0.jar
Download https://jcenter.bintray.com/net/sf/kxml/kxml2/2.3.0/kxml2-2.3.0.jar
Download https://jcenter.bintray.com/com/android/tools/layoutlib/layoutlib-api/24.0.0/layoutlib-api-24.0.0.jar
Download https://jcenter.bintray.com/org/apache/httpcomponents/httpclient/4.1.1/httpclient-4.1.1.jar
Download https://jcenter.bintray.com/org/apache/httpcomponents/httpmime/4.1/httpmime-4.1.jar
Download https://jcenter.bintray.com/com/android/tools/dvlib/24.0.0/dvlib-24.0.0.jar
Download https://jcenter.bintray.com/org/apache/commons/commons-compress/1.8.1/commons-compress-1.8.1.jar
Download https://jcenter.bintray.com/com/android/tools/lint/lint-api/24.0.0/lint-api-24.0.0.jar
Download https://jcenter.bintray.com/org/ow2/asm/asm-analysis/4.0/asm-analysis-4.0.jar
Download https://jcenter.bintray.com/org/apache/httpcomponents/httpcore/4.1/httpcore-4.1.jar
Download https://jcenter.bintray.com/commons-logging/commons-logging/1.1.1/commons-logging-1.1.1.jar
Download https://jcenter.bintray.com/commons-codec/commons-codec/1.4/commons-codec-1.4.jar
Download https://jcenter.bintray.com/org/ow2/asm/asm/4.0/asm-4.0.jar
Download https://jcenter.bintray.com/com/android/tools/external/lombok/lombok-ast/0.2.2/lombok-ast-0.2.2.jar
Download https://jcenter.bintray.com/org/ow2/asm/asm-tree/4.0/asm-tree-4.0.jar
:tasks

------------------------------------------------------------
All tasks runnable from root project
------------------------------------------------------------

Android tasks
-------------
androidDependencies - Displays the Android dependencies of the project
signingReport - Displays the signing info for each variant

Build tasks
-----------
assemble - Assembles all variants of all applications and secondary packages.
assembleDebug - Assembles all Debug builds
assembleDebugTest - Assembles the Test build for the Debug build
assembleRelease - Assembles all Release builds
build - Assembles and tests this project.
buildDependents - Assembles and tests this project and all projects that depend on it.
buildNeeded - Assembles and tests this project and all projects it depends on.
clean - Deletes the build directory.

Build Setup tasks
-----------------
init - Initializes a new Gradle build. [incubating]
wrapper - Generates Gradle wrapper files. [incubating]

Help tasks
----------
components - Displays the components produced by root project 'IntentDemo'. [incubating]
dependencies - Displays all dependencies declared in root project 'IntentDemo'.
dependencyInsight - Displays the insight into a specific dependency in root project 'IntentDemo'.
help - Displays a help message.
projects - Displays the sub-projects of root project 'IntentDemo'.
properties - Displays the properties of root project 'IntentDemo'.
tasks - Displays the tasks runnable from root project 'IntentDemo' (some of the displayed tasks may belong to subprojects).

Install tasks
-------------
installDebug - Installs the Debug build
installDebugTest - Installs the Test build for the Debug build
uninstallAll - Uninstall all applications.
uninstallDebug - Uninstalls the Debug build
uninstallDebugTest - Uninstalls the Test build for the Debug build
uninstallRelease - Uninstalls the Release build

Verification tasks
------------------
check - Runs all checks.
connectedAndroidTest - Installs and runs the tests for Build 'debug' on connected devices.
connectedCheck - Runs all device checks on currently connected devices.
deviceCheck - Runs all device checks using Device Providers and Test Servers.
lint - Runs lint on all variants.
lintDebug - Runs lint on the Debug build
lintRelease - Runs lint on the Release build

Other tasks
-----------
compileDebugSources
compileDebugTestSources
compileReleaseSources

To see all tasks and more detail, run with --all.

BUILD SUCCESSFUL

Total time: 16 mins 29.847 secs
```



./gradlew build



https://bintray.com/是The fastest and most reliable way to automate the distribution of your software releases

有点意思


gradlew实际上是https://github.com/bintray/gradle-resolver

gradlew + maven 参考https://github.com/bintray/gradle-bintray-plugin


Android 任务

通用任务

将一个plugin运用到build file中时，会自动创建一系列的构建任务（build task）去运行。Java plugin和Android Plugin也都会如此。

我们对于任务的约定有以下四个：

- assemble任务，汇集所有项目输出     
- check任务，运行所有校验
- build任务，既汇集又校验        
- clean任务，清除所有项目输出

assemble, check and build任务自己本身不做任何事情，它们只是plugin锚点，真正任务的是由plugin来添加执行。

这样做的好处是，不管你在什么项目中，你都可以调用同样的命令来执行。

通过命令行，你可以得到更高级别的任务，命令如下：

	gradle tasks

Android的任务比通用的四大任务多了“connectedCheck”和“deviceCheck”，这是想要让项目忽视设备是否连接，正常执行check任务。

- assemble任务，  汇集所有项目输出
- check任务，运行所有校验
- connectedCheck任务，运行所有需要链接设备或模拟器的校验, 并行运行
- deviceCheck任务，运行调用远程设备的校验，运用于CI Servers
- build任务，既汇集又校验
- clean任务，清除所有项目输出

注：build任务不依赖与deviceCheck或connectedCheck

more

- https://github.com/JFrogDev/build-info
- 【Sample projects for training and testing CI setup with Artifactory】https://github.com/JFrogDev/project-examples


## 安装驱动

我的设备是三星的s5，所以安装Kies for mac。

http://124.192.132.142/tech.down.sina.com.cn/20141121/361ad796/KiesMacSetup.dmg?fn=&ssig=MWlIaJQ0CZ&Expires=1421131379&KID=sae,230kw3wk15&ip=1421052179,118.244.190.41&corp=1


```
expord ANDROID_SDK_HOME=/Users/sang/Library/Android/sdk

export PATH=$PATH:$ANDROID_SDK_HOME/tools
export PATH=$PATH:$ANDROID_SDK_HOME/platform-tools
export PATH=$PATH:$ANDROID_SDK_HOME/build-tools/21.1.2
```


http://airdroid.com/en/





HoRNDIS: USB tethering driver for Mac OS X

http://joshuawise.com/horndis


## R

R是resource的意思，比如

### 获得应用名称

```
R.string.app_name
```

### 变更布局

```
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.first_layout);
}
```


## Question

###  Android开发中的Activity和ActionBarActivity有什么区别

http://zhidao.baidu.com/link?url=zAKtzY_Joi6yXB0sxVHYdZEPdhTVeZLq8E5rymhkBG0zSbWZZoTcJ_PiRHCCzaXlIJfg_910GvIN47k_XTbngkijzzap71jj60x3cJE3T8y

答案：AndroidBarActivity是支持库里的类可以兼容2.x版本 activity提供的actionbar只有在3.0以上才可以用

### versions

Error:compileSdkVersion android-21 requires compiling with JDK 7
<a href="open.sdk.settings">Open SDK Settings</a><br><a href="openFile">Open File</a>


### android -support-mutidex.jar下载地址

http://blog.csdn.net/t12x3456/article/details/40837287


## Resource

- http://romannurik.github.io/AndroidAssetStudio/index.html



## Store 


![](image/android-store.jpg)

打包使用的脚本

 https://github.com/welenwho/android-packaging-tool
 
 
## sqlite3

先输su
出现#后
输入

mount -o rw,remount /system

必须在root权限下才能挂载系统分区读写

在Android开发中，使用 adb shell 下的 sqlite3 命令来查看操作SQLite数据库时，遇到了 [ sqlite3 : not found] 问题。
网上找了下问题的原因——模拟器或真机中的 /system/xbin 目录下少了sqlite3 这个文件。
 
解决方法，步骤如下：

（1）让/system文件夹可读写

  # su
  # mount -o remount,rw -t yaffs2 /dev/block/mtdblock3 /system
  # chmod 777 xbin
 
（2）导入所需的sqlite3文件到/system/xbin目录。
（可以新建个模拟器，从/system/xbin中导出sqlite3，即可得到sqlite3文件;或者从另外一个有sqlite3文件的机器中导出获得）

  # adb push sqlite3 /system/xbin
  

  4030 KB/s (78436 bytes in 0.019s)
 
（3）修改 sqlite3 权限
  
  # chmod 4755 /system/xbin/sqlite3

（4）设置 /system为只读文件 

  # mount -o remount,ro -t yaffs2 /dev/block/mtdblock3 /system


（5）至此，就可以使用 sqlite3 命令来操作 SQLite 数据库了。


## copy for 模拟器

```
adb pull /system/xbin/add-property-tag
adb pull /system/xbin/check-lost+found
adb pull /system/xbin/cpueater
adb pull /system/xbin/cpustats
adb pull /system/xbin/daemonize
adb pull /system/xbin/dexdump
adb pull /system/xbin/directiotest
adb pull /system/xbin/iperf3
adb pull /system/xbin/kexecload
adb pull /system/xbin/ksminfo
adb pull /system/xbin/latencytop
adb pull /system/xbin/librank
adb pull /system/xbin/memtrack
adb pull /system/xbin/memtrack_share
adb pull /system/xbin/micro_bench
adb pull /system/xbin/micro_bench_static
adb pull /system/xbin/nc
adb pull /system/xbin/netperf
adb pull /system/xbin/netserver
adb pull /system/xbin/procmem
adb pull /system/xbin/procrank
adb pull /system/xbin/puncture_fs
adb pull /system/xbin/rawbu
adb pull /system/xbin/sane_schedstat
adb pull /system/xbin/showmap
adb pull /system/xbin/showslab
adb pull /system/xbin/sqlite3
adb pull /system/xbin/strace
adb pull /system/xbin/su
adb pull /system/xbin/taskstats
adb pull /system/xbin/tcpdump
adb pull /system/xbin/timeinfo
```

对于真机是没有用的




sqlite3 /data/data/com.example.sang.helloworld/databases/test.db


## 下载数据库

adb shell
su
chmod 777 /data/data/com.example.sang.helloworld/databases/*
adb pull /data/data/com.example.sang.helloworld/databases/test.db


## log sqlite

http://angeldevil.me/2014/07/24/Android-SQLite-Debug/

调试SQLite的神器，再也不用自己去打Log了，只需简单的几个命令。

adb shell setprop log.tag.SQLiteLog V
adb shell setprop log.tag.SQLiteStatements V
adb shell stop
adb shell start


结果如下所示

V/SQLiteStatements( 4405): /data/data/[package]/databases/[db_name].db: "UPDATE [table_name] SET state=-1 WHERE note_id='7556'"


想关闭Log也很简单，把上面代码中的V改为""就行了

说明在源码SQLiteDebug.java中


## 推荐sqlite editor

如果能够http可以下载就最好了

## sqlite-unique-constraint-syntax-multiple-columns-fields

http://alvinalexander.com/android/sqlite-unique-constraint-syntax-multiple-columns-fields


## 单例
http://www.androiddesignpatterns.com/2012/05/correctly-managing-your-sqlite-database.html



## 修改快捷键

- favorite是command + 2
- structure是command + 7

不方便阿，所以还是需要改过来



## 设置背景色

法2（推荐）

viewHolder.relativeLayout
					.setBackgroundResource(R.color.select_city_child_bg);
          
法1

.setBackgroundResource(Color.parseColor("#121321"));



## 最简单也最难——如何获取到Android控件的高度

http://www.2cto.com/kf/201410/341592.html


问题

如何获取一个控件的长和高，相信很多朋友第一眼看见这个问题都会觉得很简单，直接在onCreate里面调用getWidth、getMeasuredWidth不就可以获得了吗，但是，事实上是并没有简单的，不信的话，你可以去试一下，在onCreate里面，你是无法获得长宽值的，始终为0。

原因

这是为什么呢，其实熟悉view绘制流程的朋友应该一眼就看出来了，在onCreate中，我们的控件其实还并没有画好，换句话说，等onCreate方法执行完了，我们定义的控件才会被度量(measure)，所以我们在onCreate方法里面通过view.getHeight()获取控件的高度或者宽度肯定是0。

解决

No1：

```
int w = View.MeasureSpec.makeMeasureSpec(0,
                View.MeasureSpec.UNSPECIFIED);
        int h = View.MeasureSpec.makeMeasureSpec(0,
                View.MeasureSpec.UNSPECIFIED);
        imageView.measure(w, h);
        int height = imageView.getMeasuredHeight();
        int width = imageView.getMeasuredWidth();
```


这种方法很简单，就是我们自己来测量


No2：

```
ViewTreeObserver vto = imageView.getViewTreeObserver(); 
        vto.addOnPreDrawListener(new ViewTreeObserver.OnPreDrawListener() { 
            public boolean onPreDraw() { 
                vto.removeOnPreDrawListener(this);
                int height = imageView.getMeasuredHeight(); 
                int width = imageView.getMeasuredWidth(); 
                return true; 
            } 
        });
```

这个方法，我们需要注册一个ViewTreeObserver的监听回调，这个监听回调，就是专门监听绘图的，既然是监听绘图，那么我们自然可以获取测量值了，同时，我们在每次监听前remove前一次的监听，避免重复监听。



No3：

```
ViewTreeObserver vto = imageView.getViewTreeObserver();   
vto.addOnGlobalLayoutListener(new OnGlobalLayoutListener() { 
    @Override  
    public void onGlobalLayout() { 
        imageView.getViewTreeObserver().removeGlobalOnLayoutListener(this); 
        imageView.getHeight();
        imageView.getWidth();
    }   
});
```

这个方法于第2个方法基本相同，但他是全局的布局改变监听器，所以是最推荐使用的。


OK，现在看来，看似简单问题也不是那么简单吧。

以上。



## Android fill_parent、wrap_content和match_parent的区别

 三个属性都用来适应视图的水平或垂直大小，一个以视图的内容或尺寸为基础的布局比精确地指定视图范围更加方便。
1）fill_parent
设置一个构件的布局为fill_parent将强制性地使构件扩展，以填充布局单元内尽可能多的空间。这跟Windows控件的dockstyle属性大体一致。设置一个顶部布局或控件为fill_parent将强制性让它布满整个屏幕。

2） wrap_content
设置一个视图的尺寸为wrap_content将强制性地使视图扩展以显示全部内容。以TextView和ImageView控件为例，设置为wrap_content将完整显示其内部的文本和图像。布局元素将根据内容更改大小。设置一个视图的尺寸为wrap_content大体等同于设置Windows控件的Autosize属性为True。

3）match_parent
   Android2.2中match_parent和fill_parent是一个意思 .两个参数意思一样，match_parent更贴切，于是从2.2开始两个词都可以用。那么如果考虑低版本的使用情况你就需要用fill_parent了
   
## android开发设置ExpandableListView 默认是展开的

先实例化 exListView
然后
     exListView.setAdapter(exlvAdapter);
     //将所有项设置成默认展开
     int groupCount = exListView.getCount();
     for (int i=0; i< groupCount; i++) {
         exListView.expandGroup(i);
    };

       
## android之回调函数的用法和意义

http://blog.csdn.net/jason0539/article/details/10168899


CallBack是回调的意思，一般称之为回调函数

百科的解释:http://baike.baidu.com/link?url=8yMUwVEFRzxR4JGMxVN_UnFgJIH4WTnsybuW5NfwgKqVKP8NtShfJnNNeY9mBzRT

用一个比较形象的例子:

你饿了,想吃饭,就一会去问你妈一声"开饭没有啊?"

这就是正常函数调用.
但是今天你妈包饺子,花的时间比较长,你跑啊跑啊,就烦了.于是你给你妈说,我先出去玩会,开饭的时候打我手机.

等过了一阵,你妈给你打电话说"开饭啦,回来吃饭吧!"
其中,你告诉你妈打手机找你,就是你把回调函数句柄保存到你妈的动作.你妈打电话叫你,就是个回调过程.

下面用一个Android中应用到"回调"的场景,来进一步解释。

```
Button button = (Button)this.findViewById(R.id.button);
button.setOnClickListener(new Button.OnClickListener() {

  //回调函数
  @override
  publicvoid onClick(View v) {
    buttonTextView.setText("按钮被点击了");
  }
});

```



##  Android 获取屏幕尺寸与密度

http://blog.csdn.net/ithomer/article/details/6688883

```
int screenWidth  = getWindowManager().getDefaultDisplay().getWidth();       // 屏幕宽（像素，如：480px） 
int screenHeight = getWindowManager().getDefaultDisplay().getHeight();      // 屏幕高（像素，如：800p）  
```

## dp2px

http://www.baidu.com/link?url=uQ2p6Gi8Ir5Ht-5cPkF_iuSFH7C4weg-SAqWMpejBfo0Yga5ORVWJa7riTGtCwNxgEGh1gzWTvGe5OBxFNprs_

   public int Dp2Px(Context context, float dp) {
        final float scale = context.getResources().getDisplayMetrics().density;
        return (int) (dp * scale + 0.5f);
    }

    public int Px2Dp(Context context, float px) {
        final float scale = context.getResources().getDisplayMetrics().density;
        return (int) (px / scale + 0.5f);
    }

## 动态设置GridView高度 

GridView mGrid= (GridView) findViewById(R.id.gridview); 
LinearLayout.LayoutParams linearParams = (LinearLayout.LayoutParams) mGrid.getLayoutParams(); // 取控件mGrid当前的布局参数
linearParams.height = 75;// 当控件的高强制设成75象素
mGrid.setLayoutParams(linearParams); // 使设置好的布局参数应用到控件mGrid2

## Android：Button同时设置OnLongClick、OnClick模拟相机长按聚焦 短按拍照的功能

问题背景：一个Button同时设置了OnLongClick和OnClick监听。达到相机拍照，第一次长按聚焦，第二次点击拍照的效果。OnLongClick是由单独的线程执行的，如果返回false，则OnLongClick执行完毕后，会自动执行OnClick。
如果设置返回true，则OnLongClick触发执行完后便不会再执行OnClick了，这正要我要达到的效果。

参考：http://www.cnblogs.com/Tiger-Dog/articles/1944791.html

## 自定义手势

http://www.2cto.com/kf/201310/253280.html



## aar

The 'aar' bundle is the binary distribution of an Android Library Project. 

http://tools.android.com/tech-docs/new-build-system/aar-format


## no android facet found


Add an android facet to your module by following below steps.

1) Go To File Menu -> Project Structure, or press (Ctrl+Alt+Shift+S) shortcut to open "Project Structure".

2) Select "Facets" which is under the "Project Settings" tab. (First column)

3) Click on "+" button which is at the top of the Second Column to add new facets.

4) Select "Android" facet from that "Add "menu which will prompt another dialog box to select a module. (Select a module to which you want to apply this facet).

5) Select your module and that's it. :)

##  Android studio AIDL 编译问题处理

Android Studio  自动生成AIDL文件 在 main/aidl目录下，与java目录同级，但是Android Studio编译是会找不到此文件，从而无法再Active中引用，需手工复制AIDL文件到 src/main/java/com..../目录下系统才会自动编译文件并生成相应的Java类。

## Service和Activity中不能显示Toast

http://www.eoeandroid.com/thread-66465-1-1.html

前几次碰到这个问题，确实郁闷了很久... log -- java.lang.RuntimeException: Can't create handler inside thread that has not called Looper.prepare()

解决办法很简单：
        Looper.prepare();

Toast.makeText(getApplicationContext(), "test", Toast.LENGTH_LONG).show();

Looper.loop();

## java-to-scala.html

http://lampwww.epfl.ch/~michelou/android/java-to-scala.html


## android sdk 里还藏有m2repository

    <repository>
        <id>android-support</id>
        <url>file://${env.ANDROID_HOME}/extras/android/m2repository</url>
    </repository>
    
有意思啊有意思


## PANIC: Could not find test.ini file in $ANDROID_AVD_HOME nor in $HOME/.android/avd

http://bbs.csdn.net/topics/390952635

导出ANDROID_AVD_HOME环境变量：

1. Windows中增加一个名为ANDROID_AVD_HOME指向%USERPROFILE%\.android\avd
    set ANDROID_AVD_HOME=%USERPROFILE%\.android\avd
2.Linux中增加一个名为ANDROID_AVD_HOME指向$HOME/.android/avd
    export ANDROID_AVD_HOME=$HOME/.android/avd
3.Macosx中增加一个名为ANDROID_AVD_HOME指向$HOME/.android/avd
    export ANDROID_AVD_HOME=$HOME/.android/avd

重启Eclipse/Android studio

