# http通信流程
1. http客户端发起请求，创建端口
2. http服务器在端口监听客户端请求
3. http服务器向客户端返回状态和内容

#http开发环节 （资源请求过程）
1. 域名解析：Chrome搜素自身的DNS缓存 //查看chrome的自身的缓存 网址处输入：chrome://net-internals/#dns
2. 搜索操作自身的DNS缓存（浏览器没有找到缓存或缓存已经失效）
3. 读取本地的HOST文件
4. 浏览器发起一个DNS的一个系统调用
     宽带运营商服务器查看本身的缓存
     运营商服务器发起一个迭代DNS解析的请求
    coy域(根域名)----com域的顶级域的ip地址----imooc.com的域的地址----找到  imooc.com的IP地址

    运营商服务器把结果返回到操作系统内核同时缓存起来 操作系统内核把结果返回到浏览器 最终浏览器拿到了
    www.imooc.com对应的IP地址
5. 浏览器获得域名对应的IP地址后，发起tcp的三次握手
6. tcp/ip连接建立起来以后，浏览器就可以向服务器发送HTTP请求 如用HTTP的GET的
   方法请求一个根域里的一个域名，协议可以用HTTP1.0的一个协议。
7. 服务端接受了这个请求，根据路径参数，经过后端的一些处理之后，把处理后的一个
   结果的数据返回给浏览器，如果是慕课网的页面就会把完整的HTML的页面代码返回给浏览器
8. 浏览器拿到了慕课网完整的HTML的页面代码，在解析和渲染这个页面的
   时候，里面的JS、CSS、图片静态资源，他们同样也是一个个HTTP请求
   都需要经过上面的主要的七个步骤。
9. 浏览器根据拿到的资源对页面进行渲染，最终把一个完整的页面呈现给了用户  