---
title: Stetho
date: 2019-11-12 13:31:21
categories: 工具
tags: Android
---

# 简介
Stetho是Facebook推出的Android应用程序的调试桥，可启用功能强大的Chrome进行调试

# 使用
### 导入依赖
```
debugImplementation 'com.facebook.stetho:stetho:1.5.1'
debugImplementation 'com.facebook.stetho:stetho-okhttp3:1.5.1'
debugImplementation 'com.facebook.stetho:stetho-urlconnection:1.5.1'
```

### 在Application中初始化

```
if (BuildConfig.DEBUG) {
    Stetho.initialize(
        newInitializerBuilder(this)
            .enableDumpapp(Stetho.defaultDumperPluginsProvider(this))
            .enableWebKitInspector(Stetho.defaultInspectorModulesProvider(this))
            .build());
}
```

### 增加网络请求拦截器（addNetworkInterceptor）
```
OkHttpClient client = new OkHttpClient.Builder()
    .addInterceptor(initLog())
    .addNetworkInterceptor(new StethoInterceptor())
    .build();
```

### Chrome地址栏输入 chrome://inspect
Remote Target中会出现正在连接的APP，点击 inspect 进入调试界面

### 注意事项
首次进入调试界面需要翻墙