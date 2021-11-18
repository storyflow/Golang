调度器会让当前goroutine 切出等待：

1. chan 收发
2. go 语句调用函数
3. 阻塞的syscall
4. gc





## 一直占用资源怎么办？

