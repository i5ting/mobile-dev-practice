# Android

## 准备

下载android studio

下载groovy，配置环境变量

下载gradle，配置环境变量

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


