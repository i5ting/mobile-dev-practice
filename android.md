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



