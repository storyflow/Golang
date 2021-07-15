

- interface 是一种类型（接口）
- Go 语言提供了另外一种数据类型即接口，它把所有的具有共性的方法定义在一起，任何其他类型只要实现了这些方法就是实现了这个接口。

- interface 变量存储的是实现者的值

- interface 的主要工作仅是提供方法名称签名,输入参数,返回类型。最终由具体的对象来实现方法，比如 struct；

## empty interface

- go 允许不带任何方法的 interface ，这种类型的 interface 叫 **empty interface**。

