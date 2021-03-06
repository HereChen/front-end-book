# npm包及私有库

## npm 包编写

npm 包通常会兼容不同的应用场景: nodejs、require.js 和浏览器. 所以会包含一段用于判断运行环境的代码, 如下.

```javascript
// from Vue.js
(function (global, factory) {
  typeof exports === 'object' && typeof module !== 'undefined' ? module.exports = factory() :
  typeof define === 'function' && define.amd ? define(factory) : (global.NPM_THING = factory());
}(this, (function () {
  'use strict';
  // code
  // return NPM_THING;
})));
```

1. 判断是否是 nodejs 环境: `typeof exports === 'object' && typeof module !== 'undefined'`.
2. 判断是否是 require.js: `typeof define === 'function' && define.amd`

其中的 `this` 指向全局变量, nodejs `this` 为 `global`, 浏览器中 `this` 为 `window`.

## 私有库方案

为了避免重复造轮子, 提供编码效率, 同时又可以避免企业内部的业务逻辑暴露, 于是对私有库有需求. 期望, 如果私有库中有, 则从私有库中下载, 否则从公开的库中下载.

npm 的包都是公开的, 提供的[企业私有化方案](https://www.npmjs.com/enterprise)是收费的. 开源方案有:

1. cnpm: <https://github.com/cnpm/cnpmjs.org>
2. sinopia: <https://github.com/rlidwka/sinopia>

两者的对比([企业私有 npm 服务器](https://www.jianshu.com/p/659fb418c9e3)):

-- | cnpm | sinopia
--- | --- | ---
系统支持 | 非windows | 全系统
安装 | 复杂 | 简单
配置 | 较多，适合个性化需求较多的 | 较少
配置——修改默认镜像 | 不支持 | 支持
存储 | mysql | 文件格式，直观
服务托管 | 默认后台运行 | pm2, doker, forever
文档资料 | 较多 | 较少
