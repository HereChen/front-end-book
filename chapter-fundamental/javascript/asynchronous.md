# 异步

异步的方法

1. setTimeout

    ```javascript
    setTimeout(() => {
      console.log('settimeout')
    })
    ```

2. `Promise`, 链式方式写异步处理

    ```javascript
    new Promise(resolve => {
      var data = 'promise';
      resolve(data);
    }, reject => {
        reject('error');
    }).then(res => {
        console.log(res);
    });
    ```

3. `async` 和 `await`, 同步的方式写异步, 可适用于异步处理之间存在依赖的情况.

    ```javascript
    const asyncFunc = async () => {
        const result = await 'async'
        return result;
    };
    asyncFunc().then(result => {
        console.log(result);
    });
    ```

## async 和 await

> [async](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function), [await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)

## 扩展

1. [理解 JavaScript 的 async/await, 边城, 2016/11/19](https://segmentfault.com/a/1190000007535316)
