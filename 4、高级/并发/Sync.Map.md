1. 空间换时间。 通过冗余的两个数据结构(read、dirty),实现加锁对性能的影响。
2. 使用只读数据(read)，避免读写冲突。
3. 动态调整，miss次数多了之后，将dirty数据提升为read。
4. double-checking。
5. 延迟删除。 删除一个键值只是打标记，只有在提升dirty的时候才清理删除的数据。
6. 优先从read读取、更新、删除，因为对read的读取不需要锁。



##  操作

| 普通 map         | sync.Map       |                   |
| ---------------- | -------------- | ----------------- |
| map 获取某个 key | map[1]         | sync.Load(1)      |
| map 添加元素     | map[1] = 10    | sync.Store(1, 10) |
| map 删除一个 key | delete(map, 1) | sync.Delete(1)    |
| 遍历 map         | for…range      | sync.Range()      |

## 双检查

一个是首先从`m.read`中加载，不存在的情况下，并且`m.dirty`中有新数据，加锁，然后从`m.dirty`中加载。



 sync.Map 里面有两个普通 map，read map主要是负责读，dirty map 是负责读和写（加锁）



## 使用常见

1. 读多写少，不适用于大量写的场景
2. 写操作也多，但是修改的 key 和读取的 key 特别不重合。