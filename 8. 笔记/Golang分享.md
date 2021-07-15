# Golang分享

[TOC]
## 一、学习效果

配置、路由、操作数据库、参数校验、包管理

## 二、学习步骤

1、搭建Go环境环境
2、了解基本语法
3、Demo练习：Go by Example
https://gobyexample.com/
4、搭建简单的WEB服务

Tip: 零零碎碎学了大概一周，有些讲的不清楚的，请指正。

## 三、前置：一些Demo
### 1、Hello World

```
package main
    
import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```    

### 2、数组
```
package main

import "fmt"

func main()  {
	var a [5]int
	fmt.Println("emp:", a)

	a[4] = 100
	fmt.Println("set:", a)
	fmt.Println("get:", a[4])

	b := [5]int{1, 2, 3, 4, 5}
	fmt.Println("get_b:", b)
}
```
### 3、指针
```
package main

import "fmt"

func zeroval(ival int) {
	ival = 0
}

// *取得指针变量指向的内存地址的值
func zeroptr(iptr *int) {
	*iptr = 0
}

func main()  {
	i := 1
	fmt.Println("init", 1)

	zeroval(i)
	fmt.Println("zeroval:", i)

	zeroptr(&i)
	fmt.Println("zeroptr:", i)

	fmt.Println("pointer", &i)
}
```
### 5、结构体


### 6、切片
```
package main

import "fmt"

func main() {
	s := make([]string, 3)
	fmt.Println("emp:", s)

	s[0] = "a"
	s[1] = "b"

	s = append(s, "d")
	s = append(s, "e", "f")

	fmt.Println("s1:", s)

	length := len(s)
	fmt.Println("len:", length)
}
```

### 7、Go-rountines
```
package main

import (
	"fmt"
	"time"
)

func f(from string) {
	time.Sleep(time.Second)
	for i := 0; i < 3; i++ {
		fmt.Println(from, ":", i)
	}
}

func main() {
	f("direct")

	go f("goroutine")

	go func(msg string) {
		fmt.Println(msg)
	}("going")

	time.Sleep(time.Second)
	fmt.Println("done")
}
```

### 8、http-Servers

### 9、gin-Servers
```
package main

import (
	"github.com/gin-gonic/gin"
)

func main() {
	r := gin.Default()
	r.GET("/ping", func(context *gin.Context) {
		context.JSON(200, gin.H{
			"message": "pong",
		})
	})
	err := r.Run()
	if err != nil {
		panic(err)
	}
}
```

## 四、Web服务

## 代码规范
http://172.17.12.119:8181/docs/technology_center/technology_center-1bn944daph879

## 使用组件
1、Gin框架: 
2、GORM: http://gorm.io/

## 目录结构：
quickstart.2345.com
├── conf               ：用于存储配置文件
├── controllers        ：控制器
├── models             ：应用数据库模型
├── pkg                ：自定义第三方包
├── routers            ：路由逻辑处理
└── vendor 	           ：第三方包（外部）

## 配置
配置文件 conf/app.ini

## 数据库操作
http://gorm.io/




