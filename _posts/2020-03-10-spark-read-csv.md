---
layout: post
title: Spark读取CSV乱码问题，快速解决办法
categories: Spark
description: Spark读取CSV经常会遇到中文乱码问题，可以通过参数解决
keywords: spark读取CSV
---
在使用spark读取CSV格式文件是，由于文件自身格式可能是GBK或者GB2313，导致在读取解析时出现中文乱码问题。其实解决方法也是非常简单，只需要添加参数，指定解析格式为GBK即可，具体操作如下：

```scala
val df = spark.read.format("csv")
      .option("header", "true") // 文件中的第一行是否为列的名称
      .option("encoding","GBK") //这里设置
      .load("D:\\logData\\query_hive_54584.csv")
```

这样是不是很简单？ 看了很多帖子处理都比较繁琐，希望对大家有所帮助。