背景：
GRPC的HTTP返回值类型为uint64，返回json的情况下，uint64被转为string类型
即：字段定义为int，但是前端/其他方调用的时候为string

解决方案：
1、用float

2、尽量别用uint64/int64/fixed64, 用uint32/int32/fixed32代替

3、接口调用
1）前端：接口文档定义为string
2）golang服务端根据proto文件来解析：增加tag，表明json情况下为string
// @inject_tag: json:",string