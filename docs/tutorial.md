# 新手入门

本章针对的读者是 OFBiz 的新手，介绍了 OFBiz 应用开发流程的一些基本知识。希望新手可以通过这个教程
快速的了解开发 OFBiz 应用的一些最佳实践和代码规范，以及修改 OFBiz 代码的一些流程。这是一个关于
OFBiz 的 “HelloWorld”。 :)

## 概述

本入门教程分为6个部分：

1. 如何创建和加载定制的模块，并且添加第一个页面，在页面上显示 “这是一个练习程序”。
1. 创建一些更复杂的 GUI 模型，与已有的数据表交互，并且学习如何让 web 应用更加安全。
1. 学习如何与数据库实体（entities）进行交互，创建执行 CRUD 操作的服务（services）， 创建用于
表单验证的事件（events）。
1. 学习如何根据自定义的条件来调用自动触发的服务，通过服务组来调用多个服务，以及利用服务接口的概念来
在服务之间共享通用的参数。
1. 创建新的实体，扩展已有的实体，以及为你的应用准备 XML 数据。
1. 最后，将介绍利用 Axis 去实现客户端和服务端应用的通讯。

完成以上这些步骤之后，你将升级为 OFBiz 的开发者。

## 一些建议：

- 在写代码之前，请先阅读一下文档：
  - OFBiz 代码贡献者最佳实践
  - 代码规范
  - 最佳实践
- 不要只是简单的复制粘贴文件
- 可以在[这个页面](https://cwiki.apache.org/confluence/display/OFBADMIN/OFBiz+Documentation+Index)搜索想要的文档
- 养成查看 console 日志的好习惯，它可以让你更容易的解决遇到的问题，同时也可以了解系统内部运行的步骤