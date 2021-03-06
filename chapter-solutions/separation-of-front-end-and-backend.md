# 前后端分离

内容简述: 简单描述前后端分离的历史状况, 明确前后端划分的原则: 后端面向数据, 前端面向用户, 在服务端引入 nodejs 可以解决的问题(应用的场景).

## 历史

1. 前后端耦合. 例如, ASP.NET Webform 和 jsp 的标记语言的写法, 每次请求由后端返回, 且后端的语言变量混在 HTML 标签中.
2. 前后端半分离. 例如, ASP.NET MVC 和 Spring MVC 视图由后端控制, V (视图) 由前端人员开发. 开发新的页面需要后端新建接口, 编程语言通常在一个工程中, and so on.
3. 前后端完全分离. 前后端通过接口联系. 前后端会有部分逻辑重合, 比如用户输入的校验, 通常后端接口也会处理一次. 前端获取数据后渲染视图, SEO 困难.

## 目标/方法

1. 后端: 数据处理; 前端: 用户交互[^slBalint2016Separation].
2. 前端向后扩展(服务端nodejs): 解决 SEO、首屏优化、部分业务逻辑复用等问题; 前端向前扩展: 实现跨终端(iOS和Android, H5, PC)代码复用.

解决的问题:

1. core: 优化交互体验, 提高编码效率.
2. SEO.
3. 性能优化.
4. 首屏优化.
5. 代码复用(业务逻辑, 路由, 模板).

## 应用

1. 服务端框架: [Koa](https://github.com/koajs/koa), [Express](https://github.com/expressjs/express).
2. 同构框架支持: nuxt.js(可用 Koa 替换 Express).
3. 路由用 history mode (Vue.js), 如果后端不配置, 直接进入页面无法访问. 可复用模板, 直接访问时后端渲染, 路由访问时前端渲染[^slHerman2016Separation].
4. 服务端, 浏览器端及Native端都可应用的第三方库: axios, moment.js.

## 引入 nodejs 层的应用场景

除了上面所述的性能和SEO等问题, 还可以作为中间件, 抹平同类型系统的差异, 构建统一的平台.

比如, 对于多个定制化的产品, 每个产品都对应有运营平台, 用于观测用户使用情况. 由于历史上造成的差异, 每个运营平台都需要重新构建一套运行于浏览器端的前端工程. 对于这种业务相似度较高的情况, 就可以在服务端引入 nodejs, 构建统一的平台, 抹平已有系统之前的差异(比如接口有不同的风格), 只需要实现一套 Web APP. 同时也方便了后期其他定制产品的扩展.

## 阅读

* [美团点评点餐, 美团点评点餐 Nuxt.js 实战, 2017-08-09](https://juejin.im/post/598aabe96fb9a03c335a8dde)
* [Jason Strimpel, Maxime Najim, 同构JavaScript应用开发, 2017](https://book.douban.com/subject/27183584/)
* [Nicholas C. Zakas, Node.js and the new web front-end, 2013-10-07](https://www.nczonline.net/blog/2013/10/07/node-js-and-the-new-web-front-end/)

[^slBalint2016Separation]: [Balint Sera, On the separation of front-end and backend, 2016-06-15](https://medium.com/@balint_sera/on-the-separation-of-front-end-and-backend-7a0809b42820)
[^slHerman2016Separation]: [赫门, 淘宝前后端分离实践, 2014](http://2014.jsconf.cn/slides/herman-taobaoweb/#/)
