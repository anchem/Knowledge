# Java IO

## IO

传统IO基于**字节流**和**字符流**进行操作。

## NIO

NIO有4大核心抽象概念，**Buffer**、**Charsets**、**Channel**和**Selector**。

### Buffer

是数据的容器，每一种容器指定了可以处理的数据类型，Java 的基本数据类型都有其对应的 Buffer，比如`CharBuffer`、`IntBuffer`。（布尔值类型没有）

每种 Buffer 提供了一些`get`和`put`方法集用于将数据移至或移出 Buffer。

**Byte**类型的 Buffer 比较特殊，因为它们可以作为 IO 的源或目的，并同时提供其他 Buffer 所没有的能力。

### Charsets

Charsets和与之相关的**decoders**和**encoders**一起使用，可以将数据在 bytes 和 Unicode 字符间做转换。

包含以下几个类：

- Charset - 字符集
- CharsetDecoder - 将字节编码为字符
- CharsetEncoder - 将字符编码为字节
- CoderResult - 描述了coder的结果
- CodingErrorAction - 定义了当转换失败时要采取的动作

#### Charset

字符集名称，每种字符集描述了在 16 位 Unicode 和 bytes 之间转换的规则。

该类定义了一些用于创建 decoder 和 encoder 的方法。也有一些静态方法用于判断是否支持某种字符集。还支持通过`CharsetProvider`来加载新的字符集。

该类的方法均为线程安全的。

常用的标准支持的字符集有：**US-ASCII**、**ISO-8859-1**、**UTF-8**

### Channel

是对连接的抽象，连接的实体是可以进行IO操作的，比如文件或者socket。

比如以下几种对 Channel 的描述：

> The ReadableByteChannel interface specifies a read method that reads bytes from the channel into a buffer; similarly, the WritableByteChannel interface specifies a write method that writes bytes from a buffer to the channel. The ByteChannel interface unifies these two interfaces for the common case of channels that can both read and write bytes. The SeekableByteChannel interface extends the ByteChannel interface with methods to query and modify the channel's current position, and its size.

> The FileChannel class supports the usual operations of reading bytes from, and writing bytes to, a channel connected to a file, as well as those of querying and modifying the current file position and truncating the file to a specific size.

### Selector

Selector 运行单线程处理多个 Channel，它提供了多路复用和非阻塞式IO的能力。

## 参考

1. https://blog.csdn.net/u011381576/article/details/79876754
