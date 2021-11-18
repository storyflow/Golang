1、请求链路传值 / 链路追踪

2、取消耗时操作，及时释放资源（主动取消，超时取消）

3、控制子goroutine的运行



## 基本使用方法

```
type Context interface {
    Deadline() (deadline time.Time, ok bool)
    Done() <-chan struct{}
    Err() error
    Value(key interface{}) interface{}
}
```



#### Done

Done 方法返回一个 Channel 对象



## 底层

**emptyCtx**

**cancelCtx**

**valueCtx**





## 注意

- context 只能自顶向下传值，反之则不可以。
- 如果有 cancel，一定要保证调用，否则会造成资源泄露，比如 timer 泄露。
- context 一定不能为 nil，如果不确定，可以使用 context.TODO()生成一个 empty 的 context。

