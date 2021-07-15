## dlv启动的三种模式

### attach

```
go build -gcflags "all=-N -l" -o juejin main.go  # 编译
./juejin  # 运行
dlv attach 19507 --headless=true --listen=:8080 --api-version=2 --accept-multiclient --log   # attach
```

### exec

exec为手动编译并执行调试的方式

### debug

debug模式自动编译并运行调试

```
dlv debug --headless --listen=:2345 --api-version=2 main.go
```

