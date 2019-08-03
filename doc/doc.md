参考：
中文注释源码: https://github.com/tuguangquan/mybatis


1. logging 适配器
    框架实现统一是自己的 log接口，再更换底层实现时候，不用各处更改代码。
    log接口适配各种（sl4j,log4j,log4j2,jdklogging）等等。
    
2. cache 装饰器
    最基本的靠 Hashmap实现,其他靠装饰
    FIFI cache
    LRU cache
    blocking cache,线程安全
    transaction cache, 
    logging cache带有日志功能
    
3. cache exector 代理了 base exector.
   从而实现 statement级别的 二级缓存
   当然一级缓存是 session级别，session关闭就没有了
   
4. mapperProxy 代理了 mapper接口
   从而实现了 接口的实例化，在session获取mapper实例时返回了代理

5. mapperProxyFactory 通过工厂生产了各个 代理mapperProxy的创建。
   屏蔽了代理创建的细节。