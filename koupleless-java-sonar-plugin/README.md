# Java 静态代码扫描规则维护文档
此文档将介绍如何维护 Java 代码扫描规则。
# 规则介绍
## 静态变量扫描
### 类
com.alipay.sofa.koupleless.sonar.plugin.java.check.variable.MajorStaticVariableCheckRule
### 规则简介
扫描静态变量，并发出告警。基座中的静态变量是常见的导致多应用模式不兼容的诱因之一，因为静态变量是全局共享的，不同应用的静态变量可能会相互影响。
不过值得注意的是，并不是所有的静态变量都一定会导致不兼容，比如：常量、JSON 序列化工厂、单例、不可变对象、锁等。
为了降低这些低风险的干扰，让开发者能更加聚焦到真正有可能的问题，我们需要设定白名单，将这些低风险的静态变量排除在扫描之外。
白名单过滤的纬度有多个，比如：变量名、变量类型、变量值、初始化方式等, 详情可以参照具体代码。
如果未来有更多的可以不告警的白名单过滤条件，PR Welcome !