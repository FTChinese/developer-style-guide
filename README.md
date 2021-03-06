# Overview

Repo: `https://github.com/FTChinese/developer-guide`

## External Links and must-read

* [JavaScript Standard Style](https://github.com/standard/standard)
* [Node.js Style Guide](https://github.com/felixge/node-style-guide)
* [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
* [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html)
* [awesome node](https://github.com/sindresorhus/awesome-nodejs)
* [SQL Style Guide](http://www.sqlstyle.guide/)
* [PHP the Right Way](http://www.phptherightway.com/)
* [PSR-2: Coding Style Guide](https://www.php-fig.org/psr/psr-2/)
* [Modern PHP](https://www.amazon.com/Modern-PHP-Features-Good-Practices/dp/1491905018)

## 原则

对于Web客户端开发，最低的要求是具备完整的功能。就是说必须在没有JS的情况下，服务器端也应该是完整的，用户即便在没有JS的浏览器中，依然可以完成所有的表单填写、可以查看到所有有权限的数据、任何错误都可以得到提示信息。这一阶段的重点工作是必须让服务器端具有完整的功能，即便体验不是很好，即便数据的处理繁复无比，也得保证做到数据的交互必须是持续的，绝不能中断。避免把业务逻辑放到浏览器中去计算，这会造成日后的开发流程不够灵活快速，尤其对于我们这种数据基本是静态的网站来说更是如此。不要先去写了客户端再去决定服务器端应该怎么做，首先从服务器端思考问题，从后向前推动，从整体上考虑解决方案。

避免自己制造标准，多了解一下计算机科学发展至今，针对各种问题都提出过哪些解决方案，是不是可以直接采用，如restful是一套非常成熟的极致了，就不要自己再去造一套API的标准了；API的权限验证已经有了OAuth 1.0、OAuth 2.0，并且被大批企业采纳考验过，就不要自己重新发明类似的机制了。

针对动态、弱类型语言，一定要约束好自己，做到：

模块化。每一个函数、每一个类，尽量独立、封装起来，放在属于自己的文件里，文件名要能够简单第表达出来这个文件是干什么用的，不要在一个文件中放毫不相干的函数、类。用文件夹、文件去组成一个有机的结构。只有模块化了，才能解偶。

解偶。每一个函数、每一个类、每一个项目，只完成一个工作、一个任务，不要试图在一个函数里试图完成n个功能，一堆if...else。从单元测试开始，写完一个函数、一个类，只调用它能不能完成一个单元测试？

从整体架构上，也需要做到解偶。数据层、UI层、逻辑层，都要相互独立，通过一致的接口来交流。要做到某一层，用完全不同的技术替换了，却不需要更改任何其他层的东西。

每种语言采用统一的项目结构。自己的项目，爱怎么写怎么写，不需要和别人交流，自己方便、自己明白就行。但是作为机构，必须使用统一的目录结构，要保证任何其他人不需要翻开代码，看一眼就明白每个文件、每个文件夹是在干什么。工程不是艺术，这个问题上不要自由发挥，创造力用在代码上。不要在项目结构上制造成本。

## 语言

虽然语言并不起决定性作用，但学习任何一门语言总是有成本的，限于人力，我们应该对语言提供有限的选择，不能因为某个人掌握了一门生僻的语言，就任由在公司使用，这会造成使用者离职后无人接手、或者寻找继任者成本极高的局面，所以语言的选择要考虑语言的学习曲线、寻找工程师的难易程度。

Golang。学习曲线低，性能高。主要做基础设施，如API、高并发场景等。已有的经验也证明了，就我们的规模而言，Golang可以用最少的资源换来极佳的效率。

Node.js。或许我们将来的主要工具，主要做Web客户端、使用规模较小的API或需要快速开发出来的原型等。目前的观察看，稍微复杂点的项目Node.js的CPU占用率很高。原因未知。

PHP。历史遗留问题导致相关工具链已经长期停留在比较老的版本，需要升级。新版本可以提供更好的性能，也更加贴近现代语言。

Java系。需要使用的情况下提倡使用Kotlin。不提倡Scalar，学习曲线陡峭，熟悉Scalar的工程师很难找到，成本太高，而语言本身高并发的特性，不管是Golang还是Kotlin都可以提供，即便在很多大公司，经常出现人员变动造成Scalar代码难以持续地维护下去。

移动端iOS用swift；Android用Kotlin，下一步或许可以采用Flutter和Dart。

其他语言，Rust、C#都很不错，但是我们不会用。Erlang、Haskell自己学可以，但是不要在公司里用，和Scalar同理。

## Architecture
```
                        database
                            |
                            |
                    +------------------+
                    |       API        |
                    +------------------+
                            |
                            |
       +-------------------------------+
       |               |               |   
       |               |               |  
       |               |               | 
 +-----------+    +-------+    +----------+
 |Web Client |    |  iOS  |    |  Android |
 +-----------+    +-------+    +----------+
       |
       |
 +---------------+
 |Browser Client |
 +---------------+
```

## Current Content

* Node.js

  * [Introduction](./nodejs/introduction.md)
  * [Project Structure](./nodejs/project-structure.md)

* Golang

  * [Introduction](./golang/introduction.md)

* MySQL

  * [Introduction](./mysql/mysql.md)

* OS and DevOps

  * [Supervisor](./unix/supervisor.md)

* Version Control

  * [SSH with Git](./version-control/ssh-with-git)
