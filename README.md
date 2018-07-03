# web 开发者实战指南

> 陈乾煜 原创整理

**为了增强阅读体验，请你在chrome浏览器下添加[Github Toc ](https://chrome.google.com/webstore/detail/github-toc/nalkpgbfaadkpckoadhlkihofnbhfhek)插件生成TOC增强阅读体验 谢谢**

## 第一章、初始web开发

[TOC]

### 1.web开发介绍

**服务端编程介绍**：

> 大多数的大型网站采用服务器端编程来在需要的时候动态展示不同的信息，这些信息通常会从服务器上的数据库中取出，然后发送给客户端，并通过一些代码（比如HTML和Javascript）展示在客户端。 
>
> 或许服务器端编程的最大益处在于它允许你对不同的用户个体展示不同的网站信息。动态网站可以高亮基于用户喜好和习惯的与用户相关度更高的内容。服务器端编程可以通过存储偏好设置和其他个人信息来让网站更加简洁——比如通过重复使用信用卡的详细信息来简化后续付款流程。 
>
> 它甚至可以允许和用户的线下互动，比如通过邮件或者其他渠道发送通知和更新信息。服务器端的所有的这些能力使得网站可以与用户有更深的联系。
>
> 在当今这样一个网络发达的时代，学习服务器端编程是很被推荐的。

**服务端编程是什么**？

> 网络浏览器通过**超文本传输协议** ([HTTP](https://developer.mozilla.org/en-US/docs/Glossary/HTTP))来和[网络服务器](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/What_is_a_web_server) 进行通信。当你在网页上点击一个链接，或提交一个表单，再或进行一次搜索时，一个**HTTP请求**就从你的浏览器发送到了目标服务器。 
>
> 这个请求包括一个标识所请求资源的URL，一个定义所需操作的方法(比如获取，删除或者发布资源)，还可以包括编码在URL参数中的附加信息。附加信息以键值对（参数和它的值）的形式，通过一个[查询字符串](https://en.wikipedia.org/wiki/Query_string)，作为POST数据（由[HTTP POST方法](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/POST)发送）或存放在 [associated cookies](https://developer.mozilla.org/en-US/docs/Glossary/Cookie)中。 
>
> 网络服务器等待客户端的请求信息，在它们到达的时候处理它们，并且回复网络浏览器一个**HTTP回应**信息。这个回应包含一个提示请求是否成功的状态码（比如“HTTP/1.1 200 OK”代表请求成功）。 
>
> 相应一个请求的成功回应包含被请求的资源（比如一个新的HTML页面，或者图片等），然后这些会被展示在客户端的网络浏览器上。 

**服务器端编程和客户端编程是一样的吗**？

> 让我们将注意力转向涉及服务器端编程和客户端编程的代码。在每一个情况下，代码都是显然不同的：
>
> - 它们有不同的目的和关注点。
> - 它们通常不会使用相同的编程语言（Javascript是一个特例，它既可以被用在服务器端也可以被用在客户端）。
> - 它们在不同的操作系统环境中运行。
>
> 在浏览器端运行的代码被称为**客户端代码**，并且主要涉及所呈现的网页的外观和行为的改进。这就包括选择和设计UI元素、布局、导航、表单验证等。相反的，服务器端网站编程主要涉及，对于相应的请求，选择所要返回给浏览器的内容。服务器端代码解决这样一些问题，比如验证提交的数据和请求、使用数据库来存储和检索信息及发送给用户正如他们所请求的的正确内容。 
>
> 客户端代码使用 [HTML](https://developer.mozilla.org/zh-CN/docs/Learn/HTML)，[CSS](https://developer.mozilla.org/zh-CN/docs/Learn/CSS)，和[JavaScript](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript) 来编写——这些代码直接在网络浏览器中运行，并且几乎没有访问底层操作系统的路径（包括访问文件系统的被限制的权限）。网络开发者无法掌控每一个用户可能使用的用来浏览网页的浏览器——不同的浏览器对客户端代码的性能提供不一致的的兼容性，然后客户端编程的一个挑战就是如何妥善处理不同浏览器的兼容性差异。 
>
> 服务器端代码可以用任何一种编程语言进行编写——比较受欢迎的服务器端编程语言包括PHP、Python、Ruby和C#。服务器端代码有充分的权限访问服务器的操作系统，并且开发者可以选择他们乐意使用的编程语言（和特定版本的语言）。 
>
> 开发者们通常会使用web框架来编写他们的代码。web框架是一个各种函数、对象、方法和其他代码结构的集合体，web框架被设计用来解决一些普遍问题，从而加速开发，并且简化在一个特定域中面临的不同类型的任务。同样的，当客户端和服务器端代码使用框架时，它们的域是不同的，因此框架也会不同。客户端web框架简化布局和演示任务，然而服务器端web框架提供大量的普通网络服务功能，不然的话你可能需要自己来实现这些功能（比如支持会话、支持用户和身份验证、简单的数据访问、模板库等）。 
>
> > **注意事项**：客户端框架通常被用来帮助加速客户端代码的开发，但是你也可以选择手写所有的代码；事实上，如果你只需要一个小型的、简单的网站UI，手写自己的代码可能更快并且更高效。相反的，你应该从来没有考虑过不使用框架而直接编写web应用程序的服务器端组件——实现一个重要的功能比如HTTP服务器真的很难直接从头开始用Python语言构建，但是一些用Python语言写的web框架，比如Django提供了开箱即用的功能，同时还包含其他很多有用的工具。 

【详解】：https://developer.mozilla.org/zh-CN/docs/learn/Server-side/First_steps/Introduction

### 2.web框架介绍

【很好的科普文-通俗易懂】：https://q1mi.github.io/Blog/2017/09/10/aboutWebframework/

【知乎】： https://zhuanlan.zhihu.com/p/32327786 

***关键词***：

[websocket](http://www.ruanyifeng.com/blog/2017/05/websocket.html)

[gevent](http://www.bjhee.com/gevent.html)

[greenlet](http://www.bjhee.com/greenlet.html)

[单元测试](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/00143191629979802b566644aa84656b50cd484ec4a7838000)

## 第二章、环境搭建

### 1.ubuntu下环境搭建

【1】https://www.jianshu.com/p/3bb01345f28a

【2】http://xiaocong.github.io/blog/2013/06/18/customize-python-dev-environment-on-ubuntu/

### 2.包管理和虚拟环境

【1】http://blog.zengrong.net/post/2169.html

【2】https://www.jianshu.com/p/eb46d00fc7ba

【3】https://www.cnblogs.com/wilber2013/p/4769467.html

## 第三章、Flask进阶

### 1.Flask的信号机制

【1】http://www.bjhee.com/flask-ad2.html

【2】http://flask123.sinaapp.com/article/53/

### 2.Flask的扩展

【1】https://wizardforcel.gitbooks.io/flask-extension-docs/content/

### 3.操作MySQL

【1】https://wing324.github.io/2017/02/25/%E4%BD%BF%E7%94%A8flask-sqlalchemy%E7%8E%A9%E8%BD%ACMySQL/

### 4.Werkzeug

> 在这个教程中，我们将一起用 Werkzeug 创建一个短网址服务。请注意，Werkzeug 并不是 一个框架，它是一个 WSGI 工具集的库，你可以通过它来创建你自己的框架或 Web 应用。 

【1】http://werkzeug-docs-cn.readthedocs.io/zh_CN/latest/tutorial.html

## 第五章、REST和Ajax

### 1.about ajax

【1】https://blog.csdn.net/OBKoro1/article/details/72832865

【2】https://www.zhihu.com/question/31305968

【3】http://blog.51cto.com/cnn237111/1038080

【4】https://www.nowcoder.com/questionTerminal/75a61e3650b04027abf11effdfe05b93

### 2.Restful

简而言之就是 **URL定位资源，用HTTP动词（GET,POST,DELETE,DETC）描述操作。** 

看Url就知道要什么 看http method就知道干什么 看http status code就知道结果如何 

> 1. REST描述的是在网络中client和server的一种交互形式；REST本身不实用，实用的是如何设计 RESTful API（REST风格的网络接口）；
> 2. Server提供的RESTful API中，URL中只使用名词来指定资源，原则上不使用动词。“资源”是REST架构或者说整个网络处理的核心。比如：
>
> ```
> http://api.qc.com/v1/newsfeed: 获取某人的新鲜; 
> 
> http://api.qc.com/v1/friends: 获取某人的好友列表;
> 
> http://api.qc.com/v1/profile: 获取某人的详细信息;
> 
> ```
>
> 1. 用HTTP协议里的动词来实现资源的添加，修改，删除等操作。即通过HTTP动词来实现资源的状态扭转：
>
>    GET    用来获取资源，
>    POST  用来新建资源（也可以用于更新资源），
>    PUT    用来更新资源，
>    DELETE  用来删除资源。比如：
>
> ```
> DELETE http://api.qc.com/v1/friends: 删除某人的好友 （在http parameter指定好友id）
> 
> POST http://api.qc.com/v1/friends: 添加好友
> 
> UPDATE http://api.qc.com/v1/profile: 更新个人资料
> 
> ```
>
> 1. Server和Client之间传递某资源的一个表现形式，比如用JSON，XML传输文本，或者用JPG，WebP传输图片等。当然还可以压缩HTTP传输时的数据（on-wire data compression）。
> 2. 用 HTTP Status Code传递Server的状态信息。比如最常用的 200 表示成功，500 表示Server内部错误等。
>
> 主要信息就这么点。最后是要解放思想，Web端不再用之前典型的PHP或JSP架构，而是改为前段渲染和附带处理简单的商务逻辑（比如AngularJS或者BackBone的一些样例）。Web端和Server只使用上述定义的API来传递数据和改变数据状态。格式一般是JSON。iOS和Android同理可得。由此可见，Web，iOS，Android和第三方开发者变为平等的角色通过一套API来共同消费Server提供的服务。

### 3.Restful十大规范

1. 在url接口中推荐使用Https协议，让网络接口更加安全（Https是Http的安全版，即HTTP下加入
   SSL层，HTTPS的安全基础是SSL，因此加密的详细内容就需要SSL（安全套接层协议））

2. 应该尽量将API部署在专用域名之下。

   > ```
   > https://api.example.com
   > ```

   如果确定API很简单，不会有进一步扩展，可以考虑放在主域名下。

   > ```
   > https://example.org/api/
   > ```

3. 版本（Versioning）

   应该将API的版本号放入URL。

   > ```
   > https://api.example.com/v1/
   > ```

   另一种做法是，将版本号放在HTTP头信息中，但不如放入URL方便和直观。[Github](https://developer.github.com/v3/media/#request-specific-version)采用这种做法。

4. 路径（Endpoint）
   路径又称"终点"（endpoint），表示API的具体网址。

   在RESTful架构中，每个网址代表一种资源（resource），所以网址中不能有动词，只能有名词，而且所用的名词往往与数据库的表格名对应。一般来说，数据库中的表都是同种记录的"集合"（collection），所以API中的名词也应该使用复数。

   举例来说，有一个API提供动物园（zoo）的信息，还包括各种动物和雇员的信息，则它的路径应该设计成下面这样。

   > - https://api.example.com/v1/zoos
   > - https://api.example.com/v1/animals
   > - https://api.example.com/v1/employees

5. HTTP动词

   对于资源的具体操作类型，由HTTP动词表示。

   常用的HTTP动词有下面五个（括号里是对应的SQL命令）。

   > - GET（SELECT）：从服务器取出资源（一项或多项）。
   > - POST（CREATE）：在服务器新建一个资源。
   > - PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。
   > - PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。
   > - DELETE（DELETE）：从服务器删除资源。

   还有两个不常用的HTTP动词。

   > - HEAD：获取资源的元数据。
   > - OPTIONS：获取信息，关于资源的哪些属性是客户端可以改变的。

   下面是一些例子。

   > - GET /zoos：列出所有动物园
   > - POST /zoos：新建一个动物园
   > - GET /zoos/ID：获取某个指定动物园的信息
   > - PUT /zoos/ID：更新某个指定动物园的信息（提供该动物园的全部信息）
   > - PATCH /zoos/ID：更新某个指定动物园的信息（提供该动物园的部分信息）
   > - DELETE /zoos/ID：删除某个动物园
   > - GET /zoos/ID/animals：列出某个指定动物园的所有动物
   > - DELETE /zoos/ID/animals/ID：删除某个指定动物园的指定动物

6. 过滤信息（Filtering）如果记录数量很多，服务器不可能都将它们返回给用户。API应该提供参数，过滤返回结果。

   下面是一些常见的参数。

   > - ?limit=10：指定返回记录的数量
   > - ?offset=10：指定返回记录的开始位置。
   > - ?page=2&per_page=100：指定第几页，以及每页的记录数。
   > - ?sortby=name&order=asc：指定返回结果按照哪个属性排序，以及排序顺序。
   > - ?animal_type_id=1：指定筛选条件

   参数的设计允许存在冗余，即允许API路径和URL参数偶尔有重复。比如，GET /zoo/ID/animals 与 GET /animals?zoo_id=ID 的含义是相同的。

7. 状态码（Status Codes）服务器向用户返回的状态码和提示信息，常见的有以下一些（方括号中是该状态码对应的HTTP动词）。

   > - 200 OK - [GET]：服务器成功返回用户请求的数据，该操作是幂等的（Idempotent）。
   > - 201 CREATED - [POST/PUT/PATCH]：用户新建或修改数据成功。
   > - 202 Accepted - [*]：表示一个请求已经进入后台排队（异步任务）
   > - 204 NO CONTENT - [DELETE]：用户删除数据成功。
   > - 400 INVALID REQUEST - [POST/PUT/PATCH]：用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的。
   > - 401 Unauthorized - [*]：表示用户没有权限（令牌、用户名、密码错误）。
   > - 403 Forbidden - [*] 表示用户得到授权（与401错误相对），但是访问是被禁止的。
   > - 404 NOT FOUND - [*]：用户发出的请求针对的是不存在的记录，服务器没有进行操作，该操作是幂等的。
   > - 406 Not Acceptable - [GET]：用户请求的格式不可得（比如用户请求JSON格式，但是只有XML格式）。
   > - 410 Gone -[GET]：用户请求的资源被永久删除，且不会再得到的。
   > - 422 Unprocesable entity - [POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误。
   > - 500 INTERNAL SERVER ERROR - [*]：服务器发生错误，用户将无法判断发出的请求是否成功。

   状态码的完全列表参见[这里](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)。

8. 错误处理（Error handling）

   如果状态码是4xx，就应该向用户返回出错信息。一般来说，返回的信息中将error作为键名，出错信息作为键值即可。

   > ```
   > {
   >     error: "Invalid API key"
   > }
   > ```

9. 返回结果针对不同操作，服务器向用户返回的结果应该符合以下规范。

   > - GET /collection：返回资源对象的列表（数组）
   > - GET /collection/resource：返回单个资源对象
   > - POST /collection：返回新生成的资源对象
   > - PUT /collection/resource：返回完整的资源对象
   > - PATCH /collection/resource：返回完整的资源对象
   > - DELETE /collection/resource：返回一个空文档

10. Hypermedia APIRESTful API最好做到Hypermedia，即返回结果中提供链接，连向其他API方法，使得用户不查文档，也知道下一步应该做什么。

    比如，当用户向api.example.com的根目录发出请求，会得到这样一个文档。

    > ```
    > {"link": {
    >   "rel":   "collection https://www.example.com/zoos",
    >   "href":  "https://api.example.com/zoos",
    >   "title": "List of zoos",
    >   "type":  "application/vnd.yourformat+json"
    > }}
    > ```

    上面代码表示，文档中有一个link属性，用户读取这个属性就知道下一步该调用什么API了。rel表示这个API与当前网址的关系（collection关系，并给出该collection的网址），href表示API的路径，title表示API的标题，type表示返回类型。

    Hypermedia API的设计被称为[HATEOAS](http://en.wikipedia.org/wiki/HATEOAS)。Github的API就是这种设计，访问[api.github.com](https://api.github.com/)会得到一个所有可用API的网址列表。

    > ```
    > {
    >   "current_user_url": "https://api.github.com/user",
    >   "authorizations_url": "https://api.github.com/authorizations",
    >   // ...
    > }
    > ```

    从上面可以看到，如果想获取当前用户的信息，应该去访问[api.github.com/user](https://api.github.com/user)，然后就得到了下面结果。

    > ```
    > {
    >   "message": "Requires authentication",
    >   "documentation_url": "https://developer.github.com/v3"
    > }
    > ```

    上面代码表示，服务器给出了提示信息，以及文档的网址。

## 第六章、网站架构

### 1.python应用服务器

> 首先，你知道什么是应用服务器吗？应用服务器通常被描述为是存在于服务器中心架构中间层的一个软件框架。
>
> 应用服务器常被看作是一个三层的应用程序，即图形用户界面（GUI）服务器，应用程序（业务逻辑）服务器，以及数据库和事务服务器，目的是为安全及状态维护、数据访问及其持久性提供服务。
>
> 对于Web应用程序，应用服务器和Web服务器运行在相同的环境中，应用服务器支持动态网页的创建和服务的部署，比如集群、故障切换、[负载均衡](http://www.codeceo.com/article/balanced-algorithm.html)等，所以开发者只要关注实现业务逻辑即可。
>
> 如果还不明白的话，不妨将它看成是一扇神奇的大门——它可以让你写的代码运行在服务器上，并和客户端上的代码相互交流，从而让你能更清楚明白地处理复杂事务。

[科普](https://segmentfault.com/q/1010000007270099)

【1】http://www.codeceo.com/article/6-python-web-server.html

### 2.web服务器nginx

【1】http://www.infoq.com/cn/news/2017/05/Web-server-contention

【2】https://www.jianshu.com/p/4b9e00408837

【3】http://blog.51cto.com/dengqi/1290292

【4】https://lufficc.com/blog/configure-nginx-as-a-web-server

### 3.缓存系统Memcache

【1】https://blog.csdn.net/eric_sunah/article/details/51612316

【2】https://www.jianshu.com/p/56e542deabb2

【3】http://www.runoob.com/memcached/memcached-tutorial.html

### 4.键值对数据库Redis

【1】http://www.cnblogs.com/wupeiqi/articles/5132791.html

【2】https://www.jianshu.com/p/2639549bedc8

【3】http://python.jobbole.com/87305/

### 5.mongodb

> **MongoDB** 是一个基于分布式文件存储的数据库。 由C++ 语言编写。 旨在为WEB 应用提供可扩展的高性能数据存储解决方案。 **MongoDB** 是一个介于关系数据库和非关系数据库之间的产品，是非关系数据库当中功能最丰富，最像关系数据库的。 
>
> MongoDB（来自于英文单词“Humongous”，中文含义为“庞大”）是可以应用于各种规模的企业、各个行业以及各类应用程序的开源数据库。作为一个适用于敏捷开发的数据库，MongoDB的数据模式可以随着应用程序的发展而灵活地更新。与此同时，它也为开发人员 提供了传统数据库的功能：二级索引，完整的查询系统以及严格一致性等等。 MongoDB能够使企业更加具有敏捷性和可扩展性，各种规模的企业都可以通过使用MongoDB来创建新的应用，提高与客户之间的工作效率，加快产品上市时间，以及降低企业成本。
>
> MongoDB是专为可扩展性，高性能和高可用性而设计的数据库。它可以从单服务器部署扩展到大型、复杂的多数据中心架构。利用内存计算的优势，MongoDB能够提供高性能的数据读写操作。 MongoDB的本地复制和自动故障转移功能使您的应用程序具有企业级的可靠性和操作灵活性。

【1】https://www.jianshu.com/p/5e6030e73718

【2】https://legacy.gitbook.com/book/jockchou/getting-started-with-mongodb/details

【3】https://segmentfault.com/a/1190000012088118

### 6.大型网站架构经验

[小谈大型网站架构设计](https://www.jianshu.com/p/0017ecce05fe)

## 第七章、系统管理

### 1.进程管理supervisor

> Supervisor ([http://supervisord.org](http://supervisord.org/)) 是一个用 Python 写的进程管理工具，可以很方便的用来启动、重启、关闭进程（不仅仅是 Python 进程）。除了对单个进程的控制，还可以同时启动、关闭多个进程，比如很不幸的服务器出问题导致所有应用程序都被杀死，此时可以用 supervisor 同时启动所有应用程序而不是一个一个地敲命令启动。 

【1】http://liyangliang.me/posts/2015/06/using-supervisor/

### 2.应用部署fabric

> Fabric是一个Python库，用于简化使用SSH的应用程序部署或系统管理任务。
>
> 它提供的操作包括：执行本地或远程shell命令，上传/下载文件，以及其他辅助功能等。

【1】https://www.jianshu.com/p/b04bd5c60441

【2】http://www.bjhee.com/fabric.html

### 3.配置管理saltstack和ansible

[轻松使用SaltStack管理成千上万台服务器（入门教程）](http://blog.51cto.com/xficc/1676968)

[SaltStack使用](http://kuring.me/post/saltstack/)

[saltstack:使用教程之一安装及客户端返回写入MySQL](https://www.cnblogs.com/zhang-shijie/p/5282222.html)

[自动化运维工具Ansible使用介绍](https://www.jianshu.com/p/1bf79764bb6f)

[Ansible中文权威指南](http://ansible-tran.readthedocs.io/en/latest/)

### 4.使用psutil

[psutil](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001511052957192bb91a56a2339485c8a8c79812b400d49000)

[psutil--跨平台的进程管理](https://www.jianshu.com/p/64e265f663f6)

### 5.使用sentry收集错误信息

[创业公司简单粗暴之路：高效利用Sentry追踪日志发现问题](http://bigsec.com/bigsec-news/wechat-20161220-Sentry)

[ Sentry](https://blog.windrunner.me/tool/sentry.html)

### 6.StatsD 和 Graphite搭建web监控

> **Graphite** 是一个企业级的监控工具，用Python 编写，采用django 框架，sqlite 数据库存储，自有简单文本协议通讯，绘图功能强大。**Graphite**由多个后端和前端组件组成。 后端组件用于存储数值型的时间序列数据。 

[StatsD！次世代系统监控的核心](http://blog.oneapm.com/apm-tech/291.html)

[StatsD 的使用小结](https://www.jianshu.com/p/f6f18cc268a4)

[使用graphite来监控业务系统](https://www.jianshu.com/p/3d98196c4290)

## 第八章、测试和持续继承

### 1.使用unittest和doctest测试

**unittest**

> 在将来修改的时候，可以极大程度地保证该模块行为仍然是正确的。 编写单元测试时，我们需要编写一个测试类，从 **unittest**.TestCase 继承。 以 test 开头的方法就是测试方法，不以 test 开头的方法不被认为是测试方法，测试的时候不会被执行。 
>
> [单元测试](https://www.liaoxuefeng.com/wikipage/00140137128705556022982cfd844b38d050add8565dcb9000)
>
> [Python必会的单元测试框架 —— unittest](https://blog.csdn.net/huilan_same/article/details/52944782)

**doctest**

> doctest 模块会搜索那些看起来像交互式会话的 Python 代码片段，然后尝试执行并验证结果 
>
> [详解](https://my.oschina.net/lionets/blog/268542)
>
> [Python测试框架doctest](http://liuchunming033.github.io/posts/2016/06/13/python-doctest.html)

### 2.使用pytest和mock

**pytest**

> pytest是python的一种单元测试框架，与python自带的unittest测试框架类似，但是比unittest框架使用起来更简洁，效率更高。 
>
> [pytest](https://blog.csdn.net/liuchunming033/article/details/46501653)

**mock**

> mock测试就是在[测试过程](https://baike.baidu.com/item/%E6%B5%8B%E8%AF%95%E8%BF%87%E7%A8%8B)中，对于某些不容易构造或者不容易获取的对象，用一个虚拟的对象来创建以便测试的测试方法。 
>
> [python mock基本使用](https://www.cnblogs.com/fnng/p/5648247.html)
>
> [Python中Mock的示例](http://python.jobbole.com/87656/)

### 3.持续集成

> 持续集成是一种软件开发实践：许多团队频繁地集成他们的工作，每位成员通常进行 日常集成，进而每天会有多种集成。每个集成会由自动的构建（包括测试）来尽可能快地 检测错误。许多团队发现这种方法可以显著的减少集成问题并且可以使团队的开发更加 快捷。 

[使用Jenkins进行Python项目的持续集成](https://www.jianshu.com/p/caa136e191cd)

[python有什么好用的持续集成工具么？](https://www.zhihu.com/question/21101280)

[持续集成](http://pythonguidecn.readthedocs.io/zh/latest/scenarios/ci.html)

## 第九章、消息队列和Celery 

### 1.使用Beanstalkd 

> Beanstalk 是一个 C 语言实现的消息队列服务。 它提供了通用的接口，最初设计的目的是通过异步运行耗时的任务来减少大量Web应用程序中的页面延迟。针对不同的语言，有不同的 Beanstalkd Client 实现。 Python 里就有 beanstalkc 等。我就是利用 beanstalkc 来作为与 beanstalkd server 通信的工具。

[Python 使用 Beanstalkd 做异步任务处理](https://www.jianshu.com/p/cc9cd2892ff8)

### 2.深入RabbitMQ 

> rabbitMQ是消息队列；想想之前的我们学过队列queue：threading queue（线程queue，多个线程之间进行数据交互）、进程Queue（父进程与子进程进行交互或者同属于同一父进程下的多个子进程进行交互）；如果两个独立的程序，那么之间是不能通过queue进行交互的,这时候我们就需要一个中间代理即rabbitMQ. 

[python之rabbitMQ](https://www.cnblogs.com/0zcl/p/6370088.html)

[python RabbitMQ队列使用（入门篇）](https://www.cnblogs.com/kerwinC/p/5967584.html)

###  3.异步任务队列Celery在Django中的使用

【1】https://www.cnblogs.com/znicy/p/5626040.html

【2】https://my.oschina.net/Kuture/blog/1611371

【3】https://zhuanlan.zhihu.com/p/22304455 

【4】http://yshblog.com/blog/163

【5】http://python.jobbole.com/88276/

## 第十章、服务化

### 1.为什么需要服务化 

【1】https://segmentfault.com/a/1190000010767455

【2】https://www.v2ex.com/t/396828

【3】http://ju.outofmemory.cn/entry/48635

[使用Python 构建服务化基础设施](http://ocgxshkaw.bkt.clouddn.com/6%E3%80%8A%E4%BD%BF%E7%94%A8%20Python%20%E6%9E%84%E5%BB%BA%E6%9C%8D%E5%8A%A1%E5%8C%96%E6%9E%B6%E6%9E%84%E4%B8%AD%E7%9A%84%E5%9F%BA%E7%A1%80%E8%AE%BE%E6%96%BD%E3%80%8B%E5%BC%A0%E5%8D%8E%E7%BF%BC.pdf)

### 2.使用Thrift 

> Thrift 是一款高性能、开源的 RPC 框架，产自 Facebook 后贡献给了 Apache，Thrift 囊括了整个 RPC 的上下游体系，自带序列化编译工具，因为 Thrift 采用的是二进制序列化，并且与 gRPC 一样使用的都是长连接建立 client 与 server 之间的通讯，相比于比传统的使用XML，JSON，SOAP等短连接的解决方案性能要快得多。

[Python RPC 之 Thrift](https://www.jianshu.com/p/82a6bdaabcd3)

[Python Thrift示例](https://blog.csdn.net/dutsoft/article/details/71178655)

[小探python thrift通信框架的设计](http://xiaorui.cc/2016/07/24/%e5%b0%8f%e6%8e%a2python-thrift%e9%80%9a%e4%bf%a1%e6%a1%86%e6%9e%b6%e7%9a%84%e8%ae%be%e8%ae%a1/)

### 3. PIDL - 豆瓣服务化实践 

[为什么豆瓣在 GitHub 上开放自己的 Code？会对国内的开源造成怎样的影响？](https://www.zhihu.com/question/22739289)

[90%产品服务化，细说豆瓣的5年变革之路](http://www.dockone.io/article/2753)

[xxx](http://airjd.com/view/iour88qv000fg4u#2)

## 第十一章、数据处理

### 1.使用MapReduce做日志分析 

### 2.使用DPark 

### 3.使用Pandas 

## 第十二章、帮助工具

### 1.IPython

### 2.Jupyter Notebook 

### 3.调试和DEBUG工具 

### 4.进阶篇: 定制基于IPython的交互解释环境 

## 第十三章、python并发编程

### 1 使用多线程 

### 2 使用Gevent 

### 3 使用多进程

### 4 使用Future  

### 5 使用asyncio 

============================================分割线========================================

待补充