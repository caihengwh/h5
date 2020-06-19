.. sectnum::
   :start: 6

##################################
学习与HTTP交互
##################################

课程须知
=========================

1. 了解HTTP协议
2. 对js的基础知识掌握

大纲
=========================
1. 使用json-server 做数据
2. 使用 fetch 发起 GET 请求

课程内容
=========================

json-server 安装和使用
**********************
1. 什么是json-server

    JSON-Server 是一个 Node 模块，可以指定一个 json 文件作为 api 的数据源。
    JSON-Server 可以直接把一个json文件托管成一个具备全RESTful风格的API,并支持跨域、jsonp、路由订制、数据快照保存等功能的 web 服务器。简而言之就是可以做临时数据库，存些mock数据做测试。

2. 安装
`
npm install -g json-server
`
3. 以作业为例


什么是fetch
**************
Fetch API 提供了一个 JavaScript接口，用于访问和操纵HTTP管道的部分，例如请求和响应。它还提供了一个全局 fetch()方法，该方法提供了一种简单，合理的方式来跨网络异步获取资源。（取代传统的XMLHttpRequest的）
这种功能以前是使用 XMLHttpRequest实现的。Fetch提供了一个更好的替代方法，可以很容易地被其他技术使用，例如 Service Workers。
Fetch 还利用到了请求的异步特性——它是基于Promise的。

为什么要用fetch
***************
传统的XMLHttpRequest请求闲的非常的杂乱，而优雅的ajax又不得不额外加载jQuery这个80K左右的框架
那么Fetch API就应势而生，提供了一种新规范，用来取代善不完美的 XMLHttpRequest 对象

- 传统的xhr请求

.. code-block:: javascript

    var xhr = new XMLHttpRequest();
    xhr.open('GET', url);
    xhr.responseType = 'json';

    xhr.onload = function() {
    console.log(xhr.response);
    };

    xhr.onerror = function() {
    console.log("Oops, error");
    };

    xhr.send();

- fetch

.. code-block:: javascript

    fetch(url).then(function(response) {
    return response.json();
    }).then(function(data) {
    console.log(data);
    }).catch(function(e) {
    console.log("Oops, error");
    });

fetch具体使用
**************

通过网络获取一个 JSON 文件并将其打印到控制台。最简单的用法是只提供一个参数用来指明想 fetch() 到的资源路径，然后返回一个包含响应结果的promise（一个 Response 对象）。

当然它只是一个 HTTP 响应，而不是真的JSON。为了获取JSON的内容，我们需要使用 json() 方法

.. code-block:: javascript

    fetch('http://example.com/movies.json')
  .then(function(response) {
    return response.json();
  })
  .then(function(myJson) {
    console.log(myJson);
  });


使用 fetch() POST JSON数据

.. code-block:: javascript

    var url = 'https://example.com/profile';
    var data = {username: 'example'};

    fetch(url, {
    method: 'POST', // or 'PUT'
    body: JSON.stringify(data), // data can be `string` or {object}!
    headers: new Headers({
        'Content-Type': 'application/json'
    })
    }).then(res => res.json())
    .catch(error => console.error('Error:', error))
    .then(response => console.log('Success:', response));

fetch注意事项
**************

1. fetch使用的promise对象可以使得我们使用同步的方式写异步函数
2. fetch api是可以结合 async 和 await 来使用的
3. fetch提供了对request和response对象的通用定义



作业
=========================
1. 下载代码：git clone https://github.com/murphylan/tutorial.git
2. 进入项目根目录后执行下列操作：

    - cd server
    - json-server db.json  (需要实现本地安装json-server)

3. 浏览器打开首页: index.html
4. 继续完成学生信息的CRUD操作

参考链接
=========================

https://www.cnblogs.com/fly_dragon/p/9150732.html
