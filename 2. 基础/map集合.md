Map 是一种无序的键值对的集合。Map 最重要的一点是通过 key 来快速检索数据，key 类似于索引，指向数据的值。



引⽤用类型，哈希表。键必须是⽀支持相等运算符 (==、!=) 类型，⽐比如 number、string、
pointer、array、struct，以及对应的 interface。值可以是任意类型，没有限制



Map 是一种集合，所以我们可以像迭代数组和切片那样迭代它。不过，Map 是无序的，我们无法决定它的返回顺序，这是因为 Map 是使用 hash 表来实现的。



- 类似其他语言中的哈希表或者字典，以key-value形式存储数据
- `Key必须是支持==或!=比较运算的类型`，不可以是函数、map或slice
- Map查找比线性搜索快得多，但比使用索引访问数据的类型慢100倍
- `Map使用make()创建`，支持 `:=` 这种简写方式
- `make([keyType]valueType, cap)`,cap表示容量，可省略
- 超出容量时会自动扩容，但尽量提供一个合理的初始值
- 使用`len()`获取元素个数
- 键值对不存在时自动添加，使用`delete()`删除某键值对
- 使用 `for range` 对map和slice进行`迭代`操作



## 语法

```
/* 声明变量，默认 map 是 nil */
var map_variable map[key_data_type]value_data_type

/* 使用 make 函数 */
map_variable := make(map[key_data_type]value_data_type)
```

