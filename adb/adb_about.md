## ADB相关

Android未root通过adb shell查看data目录下信息

[链接在此](https://testerhome.com/topics/12183)

[adb forward相关](https://blog.csdn.net/u013553529/article/details/80036227)

### 常用命令

[链接](https://www.jianshu.com/p/56fd03f1aaae)

+ adb命令启动应用

   adb shell am start  com.tuya.testlottie/com.tuya.testlottie.MainActivity 

  ---

  统计应用启动时长（adb shell am start -W ）

  adb shell am start -W com.tuya.testlottie/com.tuya.testlottie.MainActivity

  

+ 获取进程

  adb shell ps  

  adb shell ps | grep com.xxx.xxx (根据包名查询进程)

+ 结束进程

  adb shell am force-stop com.tuya.smart（根据包名结束进程）

  ###adb shell查看日志

  Android 的日志分为如下几个优先级（priority）：

  - V —— Verbose（最低，输出得最多）
  - D —— Debug
  - I —— Info
  - W —— Warning
  - E —— Error
  - F —— Fatal
  - S —— Silent（最高，啥也不输出）

  ``` adb logcat *:W
  adb logcat *:W  会将 Warning、Error、Fatal 和 Silent 日志输出。
  ```

（**注：** 在 macOS 下需要给 `*:W` 这样以 `*` 作为 tag 的参数加双引号，如 `adb logcat "*:W"`，不然会报错 `no matches found: *:W`。）

#### 按 tag 和级别过滤日志

```adb logcat ActivityManager:I MyApp:D *:S```

表示输出 tag `ActivityManager` 的 Info 以上级别日志，输出 tag `MyApp` 的 Debug 以上级别日志，及其它 tag 的 Silent 级别日志（即屏蔽其它 tag 日志）。

#### 日志格式

可以用 `adb logcat -v <format>` 选项指定日志输出格式

#### 清空日志

```
adb logcat -c
```

#### 正则过滤

```
adb logcat | grep tuya     根据tuya名进行过滤
```

#### 常用格式

//格式1：打印默认日志数据
adb logcat 

//格式2：需要打印日志详细时间的简单数据
adb logcat -v time

//格式3：需要打印级别为Error的信息
adb logcat *:E

//格式4：需要打印时间和级别是Error的信息
adb logcat -v time *:E

/格式5：将日志保存到电脑固定的位置，比如到根目录下logcat.log
adb logcat -v time > /logcat.log