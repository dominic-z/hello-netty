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

# p135
重新理解Future，Future是一个未来对象；如果一个操作是一个异步操作，那么就会返回一个Future对象，可以通过对这个future对象注册一些listener来实现回调；

例如closeFuture方法返回的是channelFuture，可以向其中注册监听器，指的就是如果未来调用了close的话，那么就就会按照这个future里注册的监听器来执行回调；

write与connect类似，返回的都是channelFuture，可以向其中注册监听器，指的都是当未来真正执行sync方法的时候，会按照当初注册的来进行回调