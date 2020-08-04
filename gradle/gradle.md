##### Gradle 日常功能收集

+ 第三方aar缓存在本地的位置

```java
 //显示依赖包的存储路径   
 task showMeCache << {
     configurations.compile.each { println it }结果
 }
```