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

export PATH=$PATH:$ANDROID_SDK_HOME/tools
export PATH=$PATH:$ANDROID_SDK_HOME/platform-tools
export PATH=$PATH:$ANDROID_SDK_HOME/build-tools/21.1.2
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


## Resource

- http://romannurik.github.io/AndroidAssetStudio/index.html

