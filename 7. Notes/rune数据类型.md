## 官方的解释

//int32的别名，几乎在所有方面等同于int32 

//它用来区分字符值和整数值

type rune = int32



## 例子

```

package main

import "fmt"

func main() {

	var str = "hello 你好"
	fmt.Println("len(str):", len(str))

}

// 输出：12
```



## 目的：

主要是用来统计字符串长度



## 其他

golang中还有一个___byte___数据类型与rune相似，它们都是用来表示字符类型的变量类型。它们的不同在于：

- byte 等同于int8，常用来处理ascii字符
- rune 等同于int32,常用来处理unicode或utf-8字符