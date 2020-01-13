### Json Marshal：将数据编码成json字符串

```
func Marshal(v interface{}) ([]byte, error)
```



在 Go 中并不是所有的类型都能进行序列化：

- JSON object key 只支持 string
- Channel、complex、function 等 type 无法进行序列化
- 数据中如果存在循环引用，则不能进行序列化，因为序列化时会进行递归
- Pointer 序列化之后是其指向的值或者是 nil

### 跳过 field

Struct tag “-” 表示跳过指定的 filed：

```
type MyStruct struct {
    SomeField string `json:"some_field"`
    Passwd string `json:"-"`
}
m := MyStruct{}
b, err := json.Marshal(m) //{"some_feild":""}
```



注意

- 只要是可导出成员（变量首字母大写），都可以转成json。因成员变量sex是不可导出的，故无法转成json。

- 如果变量打上了json标签，如Name旁边的 ``json:"name"`` ，那么转化成的json key就用该标签“name”，否则取变量名作为key，如“Age”，“HIgh”。

- `指针变量`，编码时自动转换为`它所指向的值`，如cla变量。

- json编码成字符串后就是`纯粹的`字符串

  

### Json Unmarshal：将json字符串解码到相应的数据结构

```
func Unmarshal(data []byte, v interface{}) error
```



- json字符串解析时，需要一个“接收体”接受解析后的数据，且Unmarshal时`接收体必须传递指针`。否则解析虽不报错，但数据无法赋值到接受体中。

#### 反序列化对 slice、map、pointer 的处理

我们定义一个 struct 继续对上面例子中的 `b` 进行反序列化：

```
type FamilyMember struct {
    Name    string
    Age     int
    Parents []string
}

var m FamilyMember
err := json.Unmarshal(b, &m)
```

