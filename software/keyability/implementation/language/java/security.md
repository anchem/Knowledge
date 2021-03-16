# 安全

### 敏感异常处理

如果在传递异常时未对其中的敏感信息做过滤，则易导致信息泄露，可能帮助攻击者尝试发起进一步的攻击。即使将异常封装或净化之后，原始异常里仍然包含大量有用的信息。

JDK里包含如下敏感异常（有些三方件里也存在）：

- java.io.FileNotFoundException - 泄露文件系统结构和文件名列举
- java.util.jar.JarException - 泄露文件系统结构。读取或写入 JAR 文件时，如果发生某种错误，则抛出此异常。
- java.util.MissingResourceException - 资源列举
- java.security.acl.NotOwnerException - 所有人列举。当只允许对象（如访问控制列表）的所有者修改对象，但是试图进行修改的 Principal 不是所有者时，抛出此异常。
- java.util.ConcurrentModificationException - 可能提供线程不安全的代码信息。比如对集合进行遍历的同时，修改了集合的元素，不论是单线程还是多线程，都会抛出此异常（若使用迭代器的remove方法是没问题的）。
- javax.naming.InsufficientResourcesException - 服务器资源不足（可能有利于DoS攻击）。当无法使用资源完成所请求的操作时，抛出此异常。这可能是因为服务器或客户端上的资源缺乏。
- java.net.BindException - 当不信任客户端能够选择服务器端口时造成开放端口列举。
- java.lang.OutOfMemoryError - DoS
- java.lang.StackOverflowError - DoS
- java.sql.SQLException - 数据库结构，用户名列举。

**【处理策略】**：

1. 使用安全策略。当请求资源不合法时，仅返回简洁的错误信息，将任何有用的信息都隐藏起来。
2. 限制输入。

### 签名与加密处理

敏感数据在传输过程中要放置被窃取和恶意篡改。
