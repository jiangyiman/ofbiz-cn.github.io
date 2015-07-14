# Entity 引擎

## 简介

OFBiz 的 Entity 引擎是一系列工具和模式的集合，用于对 Entity 数据进行建模和管理。在这里，Entity
指的是由一些数据字段与其他 Entity 之间的关系组成的一组数据。这个定义来源于关系型数据库的 ER 模型的
概念。Entity 引擎 的作用是简化企业级 Entity 数据的使用。其中包括对数据的定义、维护、QA、和与 Entity
相关的功能的开发。

Entity 引擎使用了很多业务层和集成层的设计模式。其中主要包括：`Business Delegate`，`Value Object`，
`Composite Entity (variation)`，`Value Object Assembler`，`Service Locator`，和 `Data Access Object`。

对这些模式的详细介绍可以参考[《Core J2EE Patterns》](http://www.corej2eepatterns.com/BusinessDelegate.htm)一书。

还有一些模式来自于[《EJB Design Patterns》](http://www.theserverside.com/news/1369776/Free-Book-EJB-Design-Patterns)一书，（作者：Floyd Marinescu ）。这些模式包括：`Data Transfer HashMap`，和 `Generic Attribute Access`。为了生成唯一的主键，Entity 引擎使用了一种被称作为 `Ethernet Key Generation` 的设计模式，
因为它使用了一种冲突检测机制来确保多个服务器可以使用同一个数据库来获取唯一主键（与具体数据库无关）。

Entity 引擎的主要目标是尽可能地减少事务性应用中与 Entity 相关的数据持久层的代码。为了实现这个目标，
所有的 `value objects` 都是用泛型来实现的，使用 map 来存储数据字段的名称和值。`get` 和 `set` 方法
接收一个 `String` 类型的代表字段名的参数，并用这个参数来验证在这个 Entity 中确实存在这样一个字段，然后
才会进行相应地 get 或者 set 操作。这种灵活度所带来的风险可以通过在Entity 引擎与应用之间定义一层 contract 而被减弱。
这些 contract 被包含在一个特殊的 xml 文件中。

用户不用编写自己的 Entity 代码，对 entity 的定义通过 xml 文件加载并被 Entity 引擎用于在应用于实际
的数据源之间强制检验一定的规则，数据源可以是一个数据库，也可以是其他类型的数据源。这些 XML 文件定义了
所有 entity 的以及其包含的字段的名称，同时也定义了与其相对应的数据表和数据列。这些 XML 文件还被用于指定
每个字段的类型，然后通过在对应的数据源字段类型文件中查找获得最终的 Java 数据类型，和 SQL 数据类型。Entity
之间的关系也是通过 XML 文件定义的。

通过将 Entity 引擎作为一个抽象层来使用，与 Entity 相关的代码就可以很容易的创建于更改。使用 Entity API
来与 Entity 交互的代码也可以用不同的方法来部署，因此 Entity 的持久化可以独立实现，而不用影响与 Entity
交互的代码。这种抽象层使用的一个例子是，只要修改一下配置文件，应用就可以由使用 JDBC 直接访问数据库的方法变为
使用 EJB 服务器和 Entity Beans 来持久化数据。类似的代码也可以用于一些特殊的数据源，比如一些 legacy 系统
通过 HTTP 或者消息服务来与数据源交互。

未完待续。

> [原始材料](https://cwiki.apache.org/confluence/display/OFBIZ/Entity+Engine+Guide)