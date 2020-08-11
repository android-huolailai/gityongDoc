##### Gradle 日常功能收集

+ 第三方aar缓存在本地的位置

```java
 //显示依赖包的存储路径   
 task showMeCache << {
     configurations.compile.each { println it }结果
 }
```

+ 打印所有的依赖

https://www.jb51.net/article/143708.htm



+ # Android gradle 动态添加模块依赖

https://www.jianshu.com/p/415fb00b4332?tdsourcetag=s_pcqq_aiomsg