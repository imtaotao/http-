# 2.URL 与 资源
本章主要介绍

- URL 语法，以及各种 URL 组件的含义及其所做的工作
- 很多 Web 客户端都支持的 URL 快捷方式，包括相对 URL 和自动扩展 URL
- URL 编码和字符规则
- 支持各种因特网信息系统的常见 URL 方案
- URL 的未来，包括 URN —— 这种框架可以在对象从一处搬移到另一处时，保持稳定的访问名称

## URL 的语法
+ 大多数 URL 方案的 URL 语法都建立在这个由 9 部分构成的通用格式上：
```
<scheme>://<user>:<password>@<host>:<port>/<path>;<params>?<query>#<frag>
```

URL 最重要的三个部分是**方案**（scheme）、**主机**（host）和**路径**（path）

+ **通用 URL 组件的描述**

| 组件  | 描述                                                                                      | 认值         |
|-----|-----------------------------------------------------------------------------------------|------------|
| 方案  | 访问服务器以获取资源时要使用哪种协议                                                                      | 无          |
| 用户  | 某些方案访问资源时需要的用户名                                                                         | 匿名         |
| 密码  | 用户名后面可能要包含的密码，中间由冒号（:）分隔                                                                | <E-mail地址> |
| 主机  | 资源宿主服务器的主机名或点分IP地址                                                                      | 无          |
| 端口  | 资源宿主服务器正在监听的端口号。很多方案都有默认端口号（HTTP的默认端口号为80）                                              | 每个方案特有     |
| 路径  | 服务器上资源的本地名，由一个斜杠（/）将其与前面的URL组件分隔开来。路径组件的语法是与服务器和方案有关的（本章稍后会讲到URL路径可以分为若干个段，每段都可以有其特有的组件 | 无          |
| 参数  | 某些方案会用这个组件来指定输入参数。参数为名/值对。URL中可以包含多个参数字段，它们相互之间以及与路径的其余部                                | 无          |
| 查询  | 某些方案会用这个组件传递参数以激活应用程序（比如数据库、公告板、搜索引擎以及其他因特网网关）。查询组件的内容没有通用格式。用字符“?”将其与URL的其余部分分隔开来      | 无          |
| 片段  | 一小片或一部分资源的名字。引用对象时，不会将frag字段传送给服务器；这个字段是在客户端内部使用的。通过字符“#”将其与URL的其余部分分隔开来                | 无          |


## URL 的快捷方式
### 相对 url
+ 相对 url 是不完整的，如果要从相对 url 中获取完整的信息，必须从另一个被称为**基础**的 url 进校解析，使用相对 url，开发者就能省略 url 中的方案、主机、和其他一些组件了

+ 基础 url 可以显示的提供，例如在 html 中的 `<base>`，用他来转换所有相对 url，还可以封装资源的基础 url，如果没有显示的发现基础 url 的话，可以将它所属资源的 url 作为基础 url

### 自动扩展 url
+ 有些浏览器会自动扩展 url，所以用户可能不需要输入一条完整的 url
+ 有**主机名的扩展**和**历史记录扩展**等

### url 字符编码和编码机制
+ 为了避免 url 信息在传输过程中被一些其他的协议给剥去一些特定字符，url 使用了较小、通用的安全字母表中的字符

+ 不安全的字符是那些**不可见**、**不可打印（包括空格符）**

+ url 为了完整性，将不安全的字符给编码为安全字符后，再进行传输，尽管有些时候不编码也没什么问题，但这不是一个好习惯

+ url 最初使用 US-ASCII 字符集，因为其历史悠久，有很好的移植性，但是为了让世界其他非罗马语言的人能够使用，url 将转义序列集成了进去

+ url 使用转义的方式编码不安全的字符，他的格式为**一个百分号**，后面跟着俩表示字符 ASCII 码的十六进制数
```
  例如 '~' 字符
  http://www.baidu.com/%7E
```

+ 保留以及受限制的字符不建议在 url 中使用

### 方案
附录A 给出了一个完整的方案列表

### 对未来的展望（url 的不足与 urn）
+ url 表示的是实际的位置，不是准确的名字，虽然 url 能准确的告诉你资源处于什么位置，但是如果资源被转移走了，那么 url 就不再是有效的了，那时，它将无法对对象进行定位

+ 如果有了对象的准确名称，不论其在何处，都可以找到这个对象，那才是完美的。为了应对这个问题，urn 出来了，无论对象搬移到何处，urn 都能为对象提供一个稳定的名称

+ **永久统一资源定位符(PURL)** 就是用 url 来实现 urn 的一个例子，详情可以见 http://purl.oclc.org

+ url 转换为 urn 是一项巨大的工程，而且标准化的进程很慢，需要很多改动，标准主体的一致性、http 应用程序的修改等。现阶段 url 还有很大的能量，而且普通用户已经很熟悉了 url 的语法，尽管 url 有一些缺陷，但是也不是现阶段最紧迫的问题，所以，在可预见的未来，因特网资源仍然会以 url 来命名


<br><br><br>
[**上一章：HTTP 的简要介绍**](./chapter_one.md)
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;
[**下一章：HTTP 报文**](./chapter_three.md)