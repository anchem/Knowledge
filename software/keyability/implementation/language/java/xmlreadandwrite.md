# XML读写

## 安全规范

凡是数据的读写一定要考虑安全问题，XML也不例外。

### 1. 禁止直接使用不可信数据来源拼接XML

### 2. 防止解析不可信来源的XML导致的外部实体（XMLExternal Entity）攻击

### 3. 防止解析不可信来源的XML导致的内部实体扩展（XML Entity Expansion）攻击

### 4. 禁止使用不安全的XSLT转换XML文件

## 常用工具 dom4J

dom4J 是一个常用的开源的xml文档处理三方件，使用说明参考[**dom4J官方文档**](https://dom4j.github.io/)即可
