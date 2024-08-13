# JavaScript

1. 字符串包含 str.indexOf(substring) !== -1 (-1表示没找到，其他数字表示具体找到的第一次出现的索引位置)
2. 表单验证 输入大于0的正整数
    ```javascript
    const reg = /^[1-9][0-9]*$/
    if (!reg.test(str)) {
      // 请输入大于0的正整数
    } else {
      // ...
    }
    ```
3. 箭头函数表达式，也属于匿名函数，但和传统匿名函数会有区别，arrow functions，https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions，https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions#%E7%AE%AD%E5%A4%B4%E5%87%BD%E6%95%B0%E8%A1%A8%E8%BE%BE%E5%BC%8F
5. 方法定义，可以使用更短的语法定义，简化 function 属性的定义，https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions#%E6%96%B9%E6%B3%95%E5%AE%9A%E4%B9%89%E8%AF%AD%E6%B3%95，https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Method_definitions
