---
title: Android Gradle
date: 2019-09-10 13:49:19
categories: Android
tags: Gradle
---

# 环境配置
```
buildTypes {
	debug {
        /* 签名类型 */
        signingConfig signingConfigs.debug
        /* 是否开启代码混淆，默认false */
        minifyEnabled false
        /* 是否应该生成可调试的apk */
        debuggable true
        /* 混淆规则配置文件 */
        proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        /* 自定义buildType */
        buildConfigField 'String', 'BASE_URL', '"http://api.debug.com/"'
    }			

    release {
        /* 签名类型 */
        signingConfig signingConfigs.release
        /* 是否开启代码混淆，默认false */
        minifyEnabled false
        /* 是否应该生成可调试的apk */
        debuggable false
        /* 移除无用的resource文件 */
        shrinkResources true
        /* 混淆规则配置文件 */
        proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        /* 自定义buildType */
        buildConfigField 'String', 'BASE_URL', '"http://api.release.com/"'
    }  
       
    /* 从给定的构建类型复制所有属性 */
    beta.initWith(release)
    beta {
        buildConfigField "String", "BASE_URL", '"http://api.beta.com/"'
        matchingFallbacks = ['beta', 'debug', 'release']
    }
}
```

编译后会生成
```
public final class BuildConfig {
  public static final boolean DEBUG = Boolean.parseBoolean("true");
  public static final String APPLICATION_ID = "com.demo.app";
  public static final String BUILD_TYPE = "debug";
  public static final String FLAVOR = "baidu";
  public static final int VERSION_CODE = 1;
  public static final String VERSION_NAME = "1.0";
  // Fields from build type: debug
  public static final String BASE_URL = "http://api.debug.com";
}
```

调用方式
```
BuildConfig.BASE_URL
```
