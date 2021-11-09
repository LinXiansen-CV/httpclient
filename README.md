# 基于http协议实现远程调用-调用第三方接口的配置和使用案例（apache httpclient、restTemplate）

    无论是微服务还是分布式服务（都是SOA，都是面向服务编程），都面临着服务间的远程调用。那么服务间的远程调用方式有哪些呢？
    常见的远程调用方式有以下几种：
    RPC：
    Remote Produce Call远程过程调用，类似的还有RMI。自定义数据格式，基于原生TCP通信，速度快，效率高。早期的webservice，现在热门的dubbo，都是RPC的典型代表。
    
    Http：
    http其实是一种网络传输协议，基于TCP，规定了数据传输的格式。现在客户端浏览器与服务端通信基本都是采用Http协议，也可以用来进行远程服务调用。缺点是消息封装臃肿，优势是对服务的提供和调用方没有任何技术限定，自由灵活，更符合微服务理念。现在热门的Rest风格，就可以通过http协议来实现。
    
    注意：
    1、我们在普通的项目中，可以使用基于http协议的客户端 Java原生HttpURLConnection、apache httpClient、Spring restTemplate（默认的基于URLConnection）、okhttp来处理调用第三方接口的业务
    2、在微服务种中一般是用OpenFeign（基于ribbo封装）来处理服务间的远程调用,因为在使用restTemplate访问远程接口的时候，我们难以将接口管理起来，当接口变动的时候我们可能会修改多处。Spring Cloud 提供OpenFeign来解决这个问题
    OpenFeign是一种声明式、模板化的HTTP客户端。在Spring Cloud中使用OpenFeign，可以做到使用HTTP请求访问远程服务，就像调用本地方法一样的，开发者完全感知不到这是在调用远程方法，更感知不到在访问HTTP请求。
