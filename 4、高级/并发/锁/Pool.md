<img src="assets/58358f16bcee0281b55299f0386e17aa-1625552290050.jpg" alt="img" style="zoom:33%;" />

Go 1.13 之前的 sync.Pool 的实现有 2 大问题：

1. 每次 GC 都会回收创建的对象。
2. 底层实现使用了 Mutex，对这个锁并发请求竞争激烈的时候，会导致性能的下降。