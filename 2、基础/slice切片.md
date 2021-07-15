slice是“动态的数组”，传值的时候他也是拷贝赋值，只是他拷贝的是内存地址，是传递指针的。slice总是指向一个底层的array，slice声明也像array一样，只是不需要长度。

## 源码

```

struct Slice
{ 				// must not move anything
	byte* array; // actual data
	uintgo len; // number of elements
	uintgo cap; // allocated number of elements
};

```

- 在go语言中是一个结构体
- 属性 len 表⽰示可⽤用元素数量，读写操作不能超过该限制。
- 属性 cap 表⽰示最⼤大扩张容量，不能超出数组限制。
- 如果 slice == nil，那么 len、cap 结果都等于 0



## 语法

```
var slice1 []type = make([]type, len)
slice1 := make([]type, len)
```

#### append

向 slice 尾部添加数据，返回新的 slice 对象。

#### reslice

所谓 reslice，是基于已有 slice 创建新 slice 对象，以便在 cap 允许范围内调整属性。

