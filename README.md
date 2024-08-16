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
3. 箭头函数表达式，也属于匿名函数，但和传统匿名函数会有区别，arrow functions，https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions#%E7%AE%AD%E5%A4%B4%E5%87%BD%E6%95%B0%E8%A1%A8%E8%BE%BE%E5%BC%8F
5. 方法定义 method definitions，可以使用更短的语法定义，简化 function 属性的定义，https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions#%E6%96%B9%E6%B3%95%E5%AE%9A%E4%B9%89%E8%AF%AD%E6%B3%95 https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Method_definitions
6. 代码缩进使用 2个空格，而不是4个空格
7. 箭头函数和匿名函数是不一样的，虽然有相似之处
8. JS中有函数、方法、静态方法的概念，例如Math.random()是静态方法
9. {}叫做空对象，mozilla文档也是这样叫
10. Math.floor(Math.random() * 数组.length) 随机获取数组索引，Math.random() 0 <= x < 1， Math.floor向下取整
11. [1,2,3]，JS中叫数组，Arrays，不像Python一般叫列表，https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Arrays
12. JS语句末尾的分号可加可不加，没必要太拘束，没必要刻意加，必须加的时候才加，不是必须的时候，随意写就好
