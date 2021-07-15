## Go vendor

```
go get github.com/kardianos/govendor
govendor init
govendor fetch github.com/gin-gonic/gin@v1.3
```

## Go modules

```
mkdir hello
cd hello 
go mod init hello 
# 此时会出现一个hello下会出现一个 go.mod 目录
# 需要下载 所有第三方包时 go mod download
# 下载第三包可以直接使用 go get need_pkg
# 下载好的依赖 和 版本 会加入到 go.mod 里面,
# 下载好的第三包 会放在到$GOPATH/pkg/mod 中
# 没有设置GOPATH的话 下载好的第三方包会放在~/go/pkg/mod
# 如果你想放在当前目前可以执行如下命令

go mod tidy
# 检测依赖的包，下载使用到的包，剔除未使用的包



# 如果你希望将第三方依赖包放至在本项目下，可以使用该命令，此时会将第三方依赖下载至vendor 目录中
go mod vendor    
```



replace

```
replace github.com/test/test => ../test
```



