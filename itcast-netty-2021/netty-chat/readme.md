# P07

这个bytebufferUtil的功能实现是通过buffer.get(index)实现的，buffer.get()会导致position+1，但是get(index)不会

# p14
`channel.read`指的是从channel里读取，`channel.write`是向channel里写

# p16
transferTo的返回值是真实transfer的数据的大小

# p24
这个例子讲的不太好
见Server.java与client.java

# P28
见代码注释

# p29
讲的很好，重点看；
1. 如果某个事件发生了，对应的key会被加入到selectedKeys里；
2. 如果这个事件没有被处理完，下次select的时候，他还会被加入到selectedKeys里；
3. 如果这个事件处理完了，如果不手动remove，这个处理完的事件的key仍然会存在于selectedKeys之中；

# p30
视频之中，报错位置是channel.read处报错，但是在mac环境里，read不会报错，而只会返回-1

# p34
案例很好，重点看；

# p37
见WriteServer代码注释

# p38

再次重复重点说一下我理解的阻塞与非阻塞：
- 网络io过程中，有两个阶段：1. 当前数据是否准备好（准备好读、写、建立链接）；2. 进行读取与写入；
- 阻塞与非阻塞的区别，指的就是第一个阶段。
- 第二个阶段真正操作的时候，肯定都是阻塞读、阻塞写、阻塞建立链接的；
- 多路复用是阻塞还是非阻塞呢？其实我理解算是阻塞吧，因为没有准备好的时候，他就阻塞在哪。

# p47
一个channel可以同时是readable也可以同时是writable；
1. 启动server与client；
2. client连接到server，并向channel里写入一些；
3. server在accept后，向该accept之后返回的channel注册进selector并监听read和write事件；
4. server在select获取到这个channel，可以看到这个channel的isReadable和isWritable都是true；

# p49
多路复用相较于阻塞，优势就在于，少量线程可以监控多个channel的状态，并且不会死等某一个channel而导致其他channel不可用；
多路复用相较于非阻塞，优势就在于，线程不必通过多次轮询来监控channel的状态；

不存在异步阻塞！异步阻塞图一啥啊！


# p50
讲解零拷贝，讲的挺好；
`transferTo`就是说，不用java的byte数组来作为用户缓存区了，所以就少了内核缓冲区与用户缓冲区的数据拷贝；
