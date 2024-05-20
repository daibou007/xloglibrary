
# 工程说明
## 解决com.github.zhetengxiang:xlogLibrary缺少arm64-v8a库问题

基于com.github.zhetengxiang:xlogLibrary,增加缺少的arm64-v8a库文件。

使用：
```
dependencies {
    implementation 'com.github.daibou007:xlogLibrary:1.0.1'
}

```

# xloglibrary
## 背景
基于tentcent/mars/xlog v1.2.6简化日志格式，

1、移除日志文件头. 

2、精简日志格式. 

原来的日志
```
^^^^^^^^^^Feb 24 2021^^^09:50:49^^^^^^^^^^[18083,18083][2021-07-18 +0800 17:18:41]
get mmap time: 4
MARS_URL: 
MARS_PATH: rb/2021-FEB
MARS_REVISION: 42a9695b
MARS_BUILD_TIME: 2021-02-24 09:50:42
MARS_BUILD_JOB: 
log appender mode:0, use mmap:1
cache dir space info, capacity:55782572032 free:49157718016 available:49006723072
log dir space info, capacity:55782572032 free:49157718016 available:49006723072
[D][2021-07-18 +80 17:18:46.756][18083, 2*][ybxiang][, , 0][Hello World 1626599926755
[D][2021-07-18 +80 17:18:48.861][18083, 2*][ybxiang][, , 0][Hello World 1626599928861
[D][2021-07-18 +80 17:18:49.140][18083, 2*][ybxiang][, , 0][Hello World 1626599929140

```
新的日志格式
```
[2021-07-13 +80 11:09:25.333][D][ybxiang]Hello World 1626145765333
[2021-07-13 +80 11:09:26.066][D][ybxiang]Hello World 1626145766066
[2021-07-13 +80 11:09:26.785][D][ybxiang]Hello World 1626145766785
```

## 使用
gradle添加依赖

1、根build.gradle添加仓库
```
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```
2、app的build.gradle添加依赖
```
dependencies {
    implementation 'com.github.zhetengxiang:xlogLibrary:1.2.6.3'
}

```
3、和app的Log日志一致
```
Log.d(TAG, "xxx")
```
