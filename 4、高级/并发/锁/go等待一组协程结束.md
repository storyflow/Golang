## sync.WaitGroup

```
package main
import (
	"fmt"
	"sync"
	"time"
)
var wg sync.WaitGroup //定义一个同步等待的组
func task(i int){
	fmt.Println("task...",i)
	//耗时操作任务，网络请求，读取文件
	time.Sleep(time.Second)
	wg.Done() //减去一个计数
}
func main(){
	for i:= 0;i<10;i++{
		wg.Add(1) //添加一个计数
		go task(i)
	}
	wg.Wait() //阻塞直到所有任务完成
	fmt.Println("over")
}
```

## 缓冲信道channel

```
package main
import (
 "fmt"
)
var ch = make(chan int,10)
func task(i int){
 fmt.Println("task...",i)
 ch <- i
}
func main(){
 for i:= 0;i<10;i++{
  go task(i)
 }
 for i:= 0;i<10;i++{
  <- ch
 }
 fmt.Println("over")
}
```

