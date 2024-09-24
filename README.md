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
13. 对象、数组解构，解构赋值，是一种语法糖，destructuring_assignment https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment  
    基本用法如下
    ```javascript
    let person = {name: "小明", age: 18}
    let scores = [99, 100, 93]
    let {name, age} = person
    let [score1, score2, score3] = scores
    console.log(name, age, score1, score2, score3)  // 输出 "小明" 18 99 100 93
    ```
14. 加法赋值运算符（+=）将右操作数的值添加到变量，并将结果分配给该变量。原来 += 可以叫 加法赋值，https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Addition_assignment    
15. 当一个 <input>、<select> 或 <textarea> 元素的 value 被修改时，会触发 input 事件。对于 type=checkbox 或 type=radio 的 input 元素，每当用户切换控件（通过触摸、鼠标或键盘）时（HTML5 规范），input 事件都应该触发。然而，历史事实并非如此。请检查兼容性，或使用 change 事件代替这些类型的元素。`https://developer.mozilla.org/zh-CN/docs/Web/API/Element/input_event`
16. `<input type="file">`  `<input type="file" multiple>` 的数据，在 .files 属性里，而不是 .value 属性里，`.files` 是 `FileList`，每个文件是 `File`，出于安全原因，无法获取到文件的绝对路径，只有个文件名，或 `.value` 假路径，尽量不要使用 .value，这个属性对于这种情况，意义不大，使用 .files。暂时无法使用JS提供绝对路径的方式来选择文件，可能 Chrome DevTools Protocol 可以，未验证。
