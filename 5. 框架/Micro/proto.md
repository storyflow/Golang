Protobuf中最基本的数据单元是message，是类似Go语言中结构体的存在.



```
protoc --proto_path=$GOPATH/pkg/mod \ # 依赖源
       --proto_path=./proto \ # proto 文件所在目录
       --micro_out=./proto --go_out=./proto \  # 输出目录
       media.proto
```



micro_out 支持自定义

micro_out默认相对路径是：go_package的路径

go_out默认相对路径是：go_package的路径

go_out 可以过滤module的路径

micro_out 相对路径和proto路径有关联， 和当前proto所在路径一致



| ProtoBuf Type | Explain                                                      |
| :------------ | :----------------------------------------------------------- |
| int32         | int32最大支持4字节的整型数字，编码负数时效率较低             |
| int64         | int32最大支持8字节的整型数字，编码负数时效率较低             |
| uint32        | uint32最大支持4字节的无符整数                                |
| uint64        | uint32最大支持8字节的无符整数                                |
| sint32        | sint32最大支持4字节的有符整数，编码负数时效率更高            |
| sint64        | sint32最大支持8字节的有符整数，编码负数时效率更高            |
| fixed32       | 不使用可变长度方式进行编码，总是传输4字节，在编码超过$2^{28}$数值的整数时效率更高 |
| fixed64       | 不使用可变长度方式进行编码，总是传输8字节，在编码超过$2^{56}$数值的整数时效率更高 |
