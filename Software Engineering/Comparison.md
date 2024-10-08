
- [数据库系统 vs 文件系统](#数据库系统-vs-文件系统)
- [OLTP vs OLAP](#oltp-vs-olap)
- [SOAP vs REST](#soap-vs-rest)
- [REST vs RPC](#rest-vs-rpc)
- [Authorization vs Authentication](#authorization-vs-authentication)
- [正向代理 vs 反向代理](#正向代理-vs-反向代理)
- [Ingress vs Egress](#ingress-vs-egress)
- [Reference](#reference)


## 数据库系统 vs 文件系统
数据库系统是文件系统的一层包装, 它们不是独立的关系, 是依赖的关系。数据库系统依赖于文件系统。
数据库系统是建立在文件系统之上的, 也就是说数据库系统中存储的数据最终都是要存在文件系统上的。

数据库系统提供了更丰富的数据操作, 很细; 文件系统只提供了简单的文件操作接口, 很粗。
以关系型数据库 (Relational Database) 为例, 提供了 SQL 语句这样的丰富的查询语言, 可以提供一些复杂的 filter,
如快速找出学生信息表中, 所有 20-24 岁的学生信息; 如果直接在文件系统上, 则需要扫描完所有的学生数据后才能找到。

一般将结构化的数据 (Structured Data) 放在数据库系统中, 把非结构化的数据放在文件系统中。

数据库系统中读取的数据, 大部分情况下 (除了被 cache 的), 都还是会到文件系统上去读取出来的。
因此两个系统的读写效率 (不考虑复杂查询) 可以认为是差不多的, 两者都是可持久化的存储系统。

- 文件系统只能提供一些简单的读写文件操作
- 数据库系统:
  1. 建立在文件系统之上
  2. 负责组织把一些数据存到文件系统
  3. 对外的接口比较方便操作数据


## OLTP vs OLAP
|              | OLTP                         | OLAP                               |
|--------------|------------------------------|------------------------------------|
| User         | Clerk, IT Professional       | Knowledge worker                   |
| Function     | day to day operations        | decision support                   |
| Design       | application-oriented         | subject-oriented (star, snowflake) |
| Data         | E-R based                    | historical, consolidated           |
| View         | current, isolated            | summarized, multi-dimensional      |
| Usage        | detailed, relational         | ad-hoc                             |
| Access       | short, simple transaction    | read mostly                        |
| Operation    | read/write, index/hash on PK | lots of scans                      |
| Size         | 100 MB-GB                    | 100 GB-TB                          |
| Metric       | transaction throughput       | query throughput, response time    |
| Unit of Work | structured, repetitive       | complex query                      |


## SOAP vs REST
__SOAP__ stands for "Simple Object Access Protocol", while __REST__ stands for "Representational State Transfer". Below is the [comparison table](https://raygun.com/blog/soap-vs-rest-vs-json/) for them:

| | SOAP | REST |
| --- | --- | --- |
| Meaning | Simple Object Access Protocol | Representational State Transfer |
| Design | Standardized protocol with pre-defined rules to follow | Architectural style with loose guidelines and recommendations |
| Approach | Function-driven (data available as services, e.g.: “getUser”) | Data-driven (data available as resources, e.g. “user”) |
| Statefulness | Stateless by default, but it’s possible to make a SOAP API stateful | Stateless (no server-side sessions) |
| Caching | API calls cannot be cached | API calls can be cached |
| Security | WS-Security with SSL support, Built-in ACID compliance | Supports HTTPS and SSL |
| Performance | Requires more bandwidth and computing power | Requires fewer resources |
| Message format | Only XML | Plain text, HTML, XML, JSON, YAML, and others |
| Transfer protocol(s) | HTTP, SMTP, UDP, and others | Only HTTP |
| Recommended for | Enterprise apps, high-security apps, distributed environment, financial services, payment gateways, telecommunication services | Public APIs for web services, mobile services, social networks |
| Advantages | High security, standardized, extensibility | Scalability, better performance, browser-friendliness, flexibility |
| Disadvantages | Poorer performance, more complexity, less flexibility | Less security, not suitable for distributed environments |


## REST vs RPC
RPC 是一类协议的统称, Restful API 是一种编码规范。Restful API 也是一种 RPC。
RPC 通常说的意思是"远程调用", RSETful API 通常指的是 "GET https://xxx/api/users/" 之类的 Web API 设计。
Web API 当然也是一种"远程调用"。


## Authorization vs Authentication
In a nutshell:
- Authentication is when an entity proves an identity
- Authorization is when an entity proves a right to access

Check [3 Common Methods of API Authentication Explained](https://nordicapis.com/3-common-methods-api-authentication-explained/) for details.


## 正向代理 vs 反向代理
- 正向代理 (forward proxy): 是一个位于客户端和目标服务器之间的服务器(代理服务器), 为了从目标服务器取得内容,
客户端向代理服务器发送一个请求并指定目标, 然后代理服务器向目标服务器转交请求并将获得的内容返回给客户端。
- 反向代理 (reverse proxy): 是指以代理服务器来接受internet上的连接请求, 然后将请求转发给内部网络上的服务器,
并将从服务器上得到的结果返回给internet上请求连接的客户端, 此时代理服务器对外就表现为一个反向代理服务器。

|            | 正向代理                                 | 反向代理                                 |
|------------|--------------------------------------|--------------------------------------|
| 代理服务器 | 代理了"客户端", 去和"目标服务器"进行交互 | 代理了"目标服务器", 去和"客户端"进行交互 |
| 架设       | 客户端架设                               | 服务器架设                               |
| 目的       | 解决访问限制                             | 提供负载均衡、安全防护                    |


## Ingress vs Egress
|            | Ingress                                                                                                                                        | Egress                                                                                                                                                                                                                      |
|------------|------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Definition | the process of data entering a network                                                                                                         | the process of data leaving a network                                                                                                                                                                                       |
| Purpose    | security, Ingress points act as the first line of defense against potential threats, such as malicious attacks or unauthorized access attempts | traffic optimization, by applying QoS policies, bandwidth shaping, and other techniques, egress points can prioritize critical data traffic, manage congestion, and ensure efficient data transmission to external networks |


## Reference
- What Is A Reverse Proxy: https://www.cloudflare.com/learning/cdn/glossary/reverse-proxy/
- 终于有人把正向代理和反向代理解释的明明白白了: https://cloud.tencent.com/developer/article/1418457
- Understanding Ingress and Egress in Networking: https://medium.com/@dipan.saha/understanding-ingress-and-egress-in-networking-how-data-flows-in-and-out-of-networks-152e816472fe
