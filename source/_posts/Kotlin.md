---
title: Kotlin
date: 2019-09-07 21:14:13
tags: Kotlin
---

# Kotlin 简介

Kotlin是一个用于现代多平台应用的静态编程语言，由JetBrains开发
Kotlin可以编译成Java字节码，也可以编译成JavaScript，方便在没有JVM的设备上运行

# 为什么选择Kotlin

### 简洁 大大减少样板代码的数量

### 安全 避免空指针异常等整个类的错误

### 互操作性 充分利用JVM、Android和浏览器现有的库

### 工具友好 可用任何Java IDE或者使用命令行构建


# 开始

## 基础语法

### 包的定义与导入

包的声明处于源文件顶部：
```
package my.demo
import kotlin.text.*
```

### 程序入口点

Kotlin 应用程序的入口点是 main 函数
```
fun main() {
	println("Hollow world")
}
```

### 函数
带有两个 Int 参数、返回 Int 的函数

```
fun sum(a: Int, b Int): Int {
	return a + b
}

fun main() {
	print("sum of 3 and 5 is")
	println(sum(3, 5))
}
// sum of 3 and 5 id 8
```

将表达式作为函数体、返回值类型自动推断的函数：
```
fun sum(a: Int, b: Int) = a + b
```

函数返回无意义的值：
```
fun printSum(a: Int, b :Int): Unit{
	println("sum of $a and $b is $(a + b)")
}
// Unit 返回类型可以省略
```


### 变量
val 只能赋值一次
```
val a: Int = 1  //立即赋值
val b = 2       //自动推断出 Int 类型
val c: Int      //如果没有初始值，类型不能省略
c = 3           //明确赋值
```

var 可重复赋值

### 字符串模板
```
fun main() {
	var a = 1
	//模板中的简单名称：
	val s1 = "a is $a"

	a = 2
	//模板中的任意表达式：
	val s2 = "${s1.replace("is, "was")}, but now is $a"
	println(s2)

	// a was 1 but now is 2
	// 将变量中s1的 is 替换成了 was
}
```

### 条件表达式
```
fun maxOf(a: Int, b: Int): Int {
	if (a > b) {
		return a
	} else {
		return b
	}
}
```

在Kotlin中 if 也可以用作表达式：
```
fun maxOf(a: Int, b: Int) = if (a > b) a else b
```

### 空值与 null 检测
当某个变量的值可以为null的时候，必须在声明处的类型后添加 ? 来标识该引用可以为空

### 类型检测与自动类型转换
is 运算符检测一个表达式是否某类型的一个实例，如果一个不可变的局部变量或属性已经判断出为某类型，那么检测后的分支中可以直接当做该类型使用，无需转换

```
fun getStringLength(obj: Any): Int? {
    if (obj is String) {
        // `obj` 在该条件分支内自动转换成 `String`
        return obj.length
    }
    // 在离开类型检测分支后，`obj` 仍然是 `Any` 类型
    return null
}


fun main() {
    fun printLength(obj: Any) {
        println("'$obj' string length is ${getStringLength(obj) ?: "... err, not a string"} ")
    }
    printLength("Incomprehensibilities")
    printLength(1000)
    printLength(listOf(Any()))
}

'Incomprehensibilities' string length is 21 
'1000' string length is ... err, not a string 
'[java.lang.Object@3af49f1c]' string length is ... err, not a string
```

### for 循环
```
val items = listOf("apple", "banana", "kiwifruit")
for (item in items) println(item)
//或者
val items2 = listOf("apple", "banana", "kiwifruit")
for (index in items.indices) println("item at $index is ${items2[index]}")
```

### while 循环
```
val items = listOf("apple", "banana", "kiwifruit")
var index = 0
while (index < items.size) {
    println("item at $index is ${items[index]}")
    index++
}

item at 0 is apple
item at 1 is banana
item at 2 is kiwifruit
```

### when 表达式
```
fun describe(obj: Any): String =
	when (obj) {
		1          -> "One"
		"Hello"    -> "Greeting"
		is Long    -> "Long"
		!is String -> "Not a string"
		else       -> "Unknown"
	}

fun main() {
    println(describe(1))
    println(describe("Hello"))
    println(describe(1000L))
    println(describe(2))
    println(describe("other"))
}

//输出
One
Greeting
Long
Not a string
Unknown
```

### 使用区间
使用 in 运算符来检测某个数字是否在指定区间内
```
fun main() {
    val x = 10
    val y = 9
    if (x in 1..y+1) {
        println("fits in range")
    }
}
//x 在 1 - 10 的区间
//输出 fits in range
```

区间迭代：
```
for (x in 1..5) {
    print(x)
}
// 12345
```

数列迭代
```
for (x in 1..10 step 2) {
    print(x)
}
println()
for (x in 9 downTo 0 step 3) {
    print(x)
}
13579
9630
```

### Collections
对集合迭代
```
fun main() {
    val items = listOf("apple", "banana", "kiwifruit")
    for (item in items) {
        println(item)
    }
}

apple
banana
kiwifruit
```

使用 in 运算符判断集合内是否包含某实例
```
fun main() {
    val items = setOf("apple", "banana", "kiwifruit")
    when {
        "orange" in items -> println("juicy")
        "apple" in items -> println("apple is fine too")
    }
}
apple is fine too
```

使用 lambda 表达式过滤 (filter) 与映射 (map) 集合
```
fun lambda() {
    val fruits = listOf("banana", "avocado", "apple", "kiwifruit")
    fruits
        .filter { it.startsWith("a") } //a开头
        .sortedBy { it }               //倒序
        .map { it.toUpperCase() }      //大写
        .forEach { println(it) }       //输出
}
APPLE
AVOCADO
```