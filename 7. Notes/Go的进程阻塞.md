## 一、使用channel实现

```
package main

import (
    "log"
    "time"
)

func main() {
    ch := make(chan int, 1)

    go func() {
        log.Println("wait 3s...")
        time.Sleep(3 * time.Second)
        ch<-1
    }()

    <-ch
}
```

## 二、使用waitGroup实现

`waiteGroup`顾名思义，是等待一组行为执行结束，利用`wg.Add()`来添加group，利用`wg.Done`或`wg.Add(-1)`来移除，`wg.Wait()`一直阻塞直到group完全释放

```
package main

import (
    "log"
    "sync"
    "time"
)

func main() {
    var wg sync.WaitGroup

    for i:=0;i<5;i++{
        wg.Add(1)
        go func(n int) {
            defer wg.Done()
            time.Sleep(3 * time.Second)
            log.Println(n)
        }(i)
    }

    wg.Wait()
}
```

## 三、阻塞os信号

如果进程被kill，很多时候我们不能立即退出，需要善后，处理类似内存信息持久化等信息。
那么在Go中如何优雅的退出进程，下面这段代码通过捕捉os信号后，进行退出前的异常处理

```
    signalChan := make(chan os.Signal, 1)
    // 捕捉 Ctrl+c 和 kill 信号，写入signalChan
    signal.Notify(signalChan, syscall.SIGINT, syscall.SIGTERM)
    // 此处执行处理逻辑
    nsqd.Main()

    // signalChan阻塞进程
    <-signalChan

    // 捕捉信号后在Exit函数中处理信息，例如内存持久化等信息防止丢失
    nsqd.Exit()
```

