---
title: Kotlin 习惯用法
date: 2019-09-08 21:45:45
categories: Kotlin
tags: Kotlin
---

# 习惯用法
一些Kotlin中广泛使用的语法习惯

## data class
```
data class Customer(val name: String, val email: String)

fun main(){
	val customer = Customer("ring", "if.f@qq.com")
	println(customer.name)
	println(customer.email)
}
```

会为 Customer 类提供以下功能：
- 所有属性的 getters (对于var定义的还有setters)
- equals()
- hashCode()
- toString()
- copy()
- 所有属性的 component1(). component2()...等

# 函数的默认参数
```
fun foo(a: Int = 0, b: String = "") {...}
```

# 过滤list
```
val list = listOf(1, 2, 3, 4, 5)
list.filter {it > 2}
```

# 检查元素是否在集合中
```
if ("abc" in list) {...}
if ("abc" !in list) {...}
```

# 遍历 map/pair型list
```
val map = mapOf(0 to "秦", 1 to "川", 2 to "小", 3 to "将")
for ((k, v) in map) println("$k -> $v")
```

# 使用单例
```
object Resource {
  val name = "ring"
}
fun main(){
  print(Resource.name)
}
```

# if not null
```
val files = File("test").listFiles()
println(files?.size) //如果不为空 打印size
files? print("空")   //如果为空 打印“空”
```



