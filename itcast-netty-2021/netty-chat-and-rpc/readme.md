# p112
这个客户端的流程是：当客户端连接到了服务端后，在客户端启动一个线程，用来发送消息等操作

# p117

原始代码有点问题，在Message类messageClasses里没有PingMassage的类信息，因此反序列化的时候有可能有问题

# p122
我理解是说，TimeOut异常还是connection异常，要看谁先触发，比如超时时间为0.001秒，那可能此时并没有找到服务器就超时了，就抛出异常了；

# p123
视频说的是promise指的就是ChannelFuture，即connect的返回值

# p129

ALLOCATOR参数是控制`ByteBuf buf = ctx.alloc().buffer();`，例如池化非池化等等；

RESV_ALLOCATOR参数是控制`public void channelRead(ChannelHandlerContext ctx, Object msg)`的msg，
指的是netty的缓冲区，即控制一些默认的handler之间传递的bytebuf的大小