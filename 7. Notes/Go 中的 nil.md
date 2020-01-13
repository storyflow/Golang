### Go 中的 nil 是一个预定义标识符

你可以使用 nil 而不用声明它.

### nil 可以表示很多类型的零值

在 Go 中, nil 可以表示以下类型的零值:

- pointer (包括类型不安全的)
- map
- slice
- function
- channel
- interface

换句话说, 在 Go 中, nil 可能是许多不同类型的值.



### nil 不是默认类型

Go 中的每个其他预定义标识符都有一个默认类型. 比如,

- true 和 false 的默认类型都是 bool 类型.
- iota 的默认类型是 int.