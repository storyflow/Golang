使用 `defer` 的最常见场景是在函数调用结束后完成一些收尾工作，例如在 `defer` 中回滚数据库的事

## 作用域

```go
func main() {
	for i := 0; i < 5; i++ {
		defer fmt.Println(i)
	}
}

$ go run main.go
4
3
2
1
0
```