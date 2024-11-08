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
15. 当一个 `<input>`、`<select>` 或 `<textarea>` 元素的 value 被修改时，会触发 input 事件。对于 type=checkbox 或 type=radio 的 input 元素，每当用户切换控件（通过触摸、鼠标或键盘）时（HTML5 规范），input 事件都应该触发。然而，历史事实并非如此。请检查兼容性，或使用 change 事件代替这些类型的元素。`https://developer.mozilla.org/zh-CN/docs/Web/API/Element/input_event`
16. `<input type="file">`  `<input type="file" multiple>` 的数据，在 .files 属性里，而不是 .value 属性里，`.files` 是 `FileList`，每个文件是 `File`，出于安全原因，无法获取到文件的绝对路径，只有个文件名，或 `.value` 假路径，尽量不要使用 .value，这个属性对于这种情况，意义不大，使用 .files。暂时无法使用JS提供绝对路径的方式来选择文件，可能 Chrome DevTools Protocol 可以，未验证。
17. 实现拖放(拖拽、放置)的简单例子。HTML 拖放（Drag and Drop）接口使应用程序能够在浏览器中使用拖放功能。例如，用户可使用鼠标选择可拖拽（draggable）元素，将元素拖拽到可放置（droppable）元素，并释放鼠标按钮以放置这些元素。拖拽操作期间，会有一个可拖拽元素的半透明快照跟随着鼠标指针。 `https://developer.mozilla.org/zh-CN/docs/Web/API/HTML_Drag_and_Drop_API`
```html
<!DOCTYPE HTML>
<html>
<head>
  <meta charset="UTF-8">
</head>
<body>

<h2>拖放</h2>
<p>在两个 div 元素之间来回拖动图像。</p>

<div id="div1" ondrop="drop(event)" ondragover="allowDrop(event)">
  <img src="" draggable="true" ondragstart="drag(event)" id="img1" width="88" height="31">
</div>

<div id="div2" ondrop="drop(event)" ondragover="allowDrop(event)"></div>

<style>
  #div1, #div2 {
    float: left;
    width: 100px;
    height: 35px;
    margin: 10px;
    padding: 10px;
    border: 1px solid black;
  }
  img {
    background-color: grey;
  }
</style>
<script>
  function allowDrop(ev) {
    ev.preventDefault();
  }

  function drag(ev) {
    ev.dataTransfer.setData("text", ev.target.id);
  }

  function drop(ev) {
    ev.preventDefault();
    var data = ev.dataTransfer.getData("text");
    ev.target.appendChild(document.getElementById(data));
  }
</script>
</body>
</html>
```
18. 和 `<input type="file" multiple>` 类似，`<select multiple>` 不能简单用 `.value`，要遍历 `.options`，检查 `checked`，然后再获取每个 option 的 `value`，当然选择的时候，也不能简单用 value，而是要选中的选项，使用 `option.selected = true`
```html
<select id="select" multiple>
  <option value="1">1111</option>
  <option value="2">2222</option>
  <option value="3">3333</option>
</select >
<script>
  const options = document.querySelector('#select').options
  const selectedValues = []
  for (let i = 0; i < options.length; i++) {
    if (options[i].selected) {
      selectedValues.push(options[i].value)
    }
  }
  // selectedValues.join(',')
</script>
```
19. 有些表单控件 `form control` 元素的 `.labels` 可以获取 这个元素的所有 `label` 元素，`label` 元素的 `.control`，可以获取这个 标签 所关联的 表单控件
20. 方便理解 Promise async await 的例子
```javascript
// 买菜 
function getFood() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      food = "马铃薯"
      console.log(food)
      resolve("马铃薯")
    }, 3 * 1000);
  })
}
// 做饭
function getDinner(food) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      dinner = food + "晚餐"
      console.log(dinner)
      resolve(dinner)
    }, 3 * 1000);
  })
}
// 吃饭
function eatDinner(dinner) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(dinner + "吃完了")
      resolve()
    }, 3 * 1000);
  })
}
// getFood()
//   .then((food) => {
//     return getDinner(food)
//   })
//   .then((dinner) => {
//     return eatDinner(dinner)
//   })
//   .then()
async function getFoodGetDinnerAndEatDinner() {
  const food = await getFood()
  const dinner = await getDinner(food)
  await eatDinner(dinner)
}

getFoodGetDinnerAndEatDinner()
```
21. `Promise` 的出现是为了解决 `Callback Hell` 问题，`async/await` 的出现是为了解决 `Promise` 处理链可能会太长并且不够直观的问题。 `https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Using_promises` `http://callbackhell.com/`
```javascript
// Callback Hell
doSomething(function (result) {
  doSomethingElse(result, function (newResult) {
    doThirdThing(newResult, function (finalResult) {
      console.log(`得到最终结果：${finalResult}`);
    }, failureCallback);
  }, failureCallback);
}, failureCallback);
// Promise 处理链
doSomething()
  .then((url) => fetch(url))
  .then((res) => res.json())
  .then((data) => {
    listOfIngredients.push(data);
  })
  .then(() => {
    console.log(listOfIngredients);
  });
// 更直观、更类似同步代码的代码
async function logIngredients() {
  const url = await doSomething();
  const res = await fetch(url);
  const data = await res.json();
  listOfIngredients.push(data);
  console.log(listOfIngredients);
}
```
22. `Promise` `async/await` 比较重要的知识点
```text
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises

A Promise is an object representing the eventual completion or failure of an asynchronous operation.
一个 Promise 对象表示一个异步操作的最终完成或者失败。（翻译的不够好）

const promise = doSomething();
const promise2 = promise.then(successCallback, failureCallback);
This second promise (promise2) represents the completion not just of doSomething(), but also of the successCallback or failureCallback you passed in — which can be other asynchronous functions returning a promise.
promise.then()调用结束返回promise2，表示 doSomething()调用完了，而且successCallback()或failureCallback()也调用完了。

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function

An async function declaration creates an AsyncFunction object.
一个 异步函数 声明 会创建一个 AsyncFunction 对象

Note: The await keyword is only valid inside async functions within regular JavaScript code. If you use it outside of an async function's body, you will get a SyntaxError.
await can be used on its own with JavaScript modules.
await 关键字 只能再 async functions 里面有效。如果再 async function body 外面用，会有 SyntaxError

In addition, the arguments to then are optional, and catch(failureCallback) is short for then(null, failureCallback)
then()的参数是可选的，catch(failureCallback) 是 then(null, failureCallback) 的简写

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

A Promise is in one of these states:
- pending: initial state, neither fulfilled nor rejected.
- fulfilled: meaning that the operation was completed successfully.
- rejected: meaning that the operation failed.
一个 Promise 对象一定是三种状态之一，待确定、已兑现、已拒绝

A promise is said to be settled if it is either fulfilled or rejected, but not pending.
一个 Promise 对象如果是已兑现或已拒绝，而不是待确定，那么也叫 settled 已敲定




todo: 理解so if your error handling code is the same for all steps, you can attach it to the end of the chain
读：https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
```
23. 逗号运算符 `,` `Comma operator` `逗号（,）运算符对它的每个操作数从左到右求值，并返回最后一个操作数的值。这让你可以创建一个复合表达式，其中多个表达式被评估，复合表达式的最终值是其成员表达式中最右边的值。` `The comma (,) operator evaluates each of its operands (from left to right) and returns the value of the last operand. ` `https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comma_operator` 例如 `module.exports = (0, _inProcessFactory.createInProcessPlaywright)();`
```javascript
const a = (1, 2, 3, 4)
const b = (1, function() { return 2; })()

console.log(a);
console.log(b);
// > node .\test.js
// 4
// 2
```
24. setImmediate()  /ɪˈmiː.di.ət/ `该方法用来把一些需要长时间运行的操作放在一个回调函数里，在浏览器完成后面的其他语句后，就立刻执行这个回调函数。` `This method is used to break up long running operations and run a callback function immediately after the browser has completed other operations such as events and display updates.` `https://developer.mozilla.org/zh-CN/docs/Web/API/Window/setImmediate` 
```text
已弃用: 不再推荐使用该特性。虽然一些浏览器仍然支持它，但也许已从相关的 web 标准中移除，也许正准备移除或出于兼容性而保留。请尽量不要使用该特性，并更新现有的代码；参见本页面底部的兼容性表格以指导你作出决定。请注意，该特性随时可能无法正常工作。

非标准: 该特性是非标准的，请尽量不要在生产环境中使用它！
```
25. 异常处理 
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw
- https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Control_flow_and_error_handling#%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86%E8%AF%AD%E5%8F%A5
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error
```javascript
// throw 语句用于抛出用户自定义的异常。当前函数的执行将停止（throw 之后的语句不会被执行），并且控制权将传递给调用堆栈中第一个 catch 块。如果调用函数中没有 catch 块，则程序将终止。
// 对于 Node.js 没有捕获异常，则程序终止，不会执行 throw 之后的语句
console.log(111);
throw new Error("出错了！");
console.log(222);
/*
C:\Users\zhouhuajian\Desktop\software\nodejs\node.exe .\demo.js
111
Process exited with code 1
Uncaught Error Error: 出错了！
    at <anonymous> (c:\Users\zhouhuajian\Desktop\temp\demo.js:2:7)
    at Module._compile (<node_internals>/internal/modules/cjs/loader:1469:14)
    at Module._extensions..js (<node_internals>/internal/modules/cjs/loader:1548:10)
    at Module.load (<node_internals>/internal/modules/cjs/loader:1288:32)
    at Module._load (<node_internals>/internal/modules/cjs/loader:1104:12)
    at executeUserEntryPoint (<node_internals>/internal/modules/run_main:174:12)
    at <anonymous> (<node_internals>/internal/main/run_main_module:28:49)
No debugger available, can not send 'variables'
*/
```
```html
<!-- 对于浏览器的JS执行环境来说，throw 后面的语句不会执行，但是事件循环还是会进入并正常运行，注意这种不一样的情况 -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>测试</title>
</head>
<body>
  <button id="btn">测试</button>
  <script>
    console.log(111);
    document.querySelector("#btn").addEventListener('click', function () {
      console.log("点击啦");
    })
    throw new Error("出错啦");
    console.log(222);
  </script>
</body>
</html>
<!-- 
控制台能输出 111 并且输出了5个 点击啦 点了5次 说明事件循环还是正常进入了

111
demo:17 Uncaught Error: 出错啦
    at demo:17:11
（匿名） @ demo:17
5 demo:15 点击啦
-->
```
```javascript
// throw expression;
// 通常下抛出 Error 或 其子类对象 比较规范，因为 捕获异常的开发人员，可能会用 message 之类的属性，message 是 Error 第一个参数的值
// 但实际上，throw 可以抛出任意对象，捕获到的对象，也是对应的对象，不一定非得是 Error 对象

throw "Error2"; // String type
throw 42; // Number type
throw true; // Boolean type
throw {
  toString: function () {
    return "I'm an object!";
  },
};
```