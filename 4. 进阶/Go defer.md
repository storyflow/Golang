go 的 defer 语句是用来**延迟执行函数的**，而且延迟发生在**调用函数 return 之后**

## defer 的重要用途一：清理释放资源

## defer 的重要用途二：执行 recover

## 多个 defer 的执行顺序

defer 的作用就是把关键字之后的函数执行压入一个栈中延迟执行，多个 defer 的执行顺序是后进先出 LIFO 

```
defer func() { fmt.Println("1") }()
defer func() { fmt.Println("2") }()
defer func() { fmt.Println("3") }()
// 123
```

