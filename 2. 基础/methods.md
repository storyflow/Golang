## 和function区别

1、类似class

2、A method is a function with a special *receiver* argument.

## 调用

结构看起来像普通结构，但 `perimeter()` 函数在函数名称之前有一个类型 `triangle` 的额外参数。 也就是说，在使用结构时，你可以按如下方式调用函数：

```
type triangle struct {
    size int
}

func (t triangle) perimeter() int {
    return t.size * 3
}

func main() {
    t := triangle{3}
    fmt.Println("Perimeter:", t.perimeter())
}
```



## 修改问题

如果要修改接收方中的任何字段，则必须在接收方中使用指针。

