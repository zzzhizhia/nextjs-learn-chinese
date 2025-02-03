# 第四章 React 入门

<!-- To use React in your newly created project, load two React scripts from an external website called [unpkg.com](https://unpkg.com/): -->

在您新创建的项目中使用 React，需要从名为 [unpkg.com](https://unpkg.com/) 的外部网站加载两个 React 脚本：

<!--
- **react** is the core React library.
- **react-dom** provides DOM-specific methods that enable you to use React with the DOM.
-->

- **react** 是 React 的核心库。
- **react-dom** 提供了与 DOM 相关的方法，使您可以将 React 用于 DOM。

```html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script type="text/javascript">
      const app = document.getElementById('app');
      const header = document.createElement('h1');
      const text = 'Develop. Preview. Ship.';
      const headerContent = document.createTextNode(text);
      header.appendChild(headerContent);
      app.appendChild(header);
    </script>
  </body>
</html>
```

<!-- Instead of directly manipulating the DOM with plain JavaScript, remove the DOM methods that you had added previously, and add the [`ReactDOM.createRoot()`](https://react.dev/reference/react-dom/client/createRoot) method to target a specific DOM element and create a root to display your React Components in. Then, add the [`root.render()`](https://react.dev/reference/react-dom/client/hydrateRoot#root-render) method to render your React code to the DOM. -->

与其使用纯 JavaScript 直接操作 DOM，请移除之前添加的 DOM 方法，并添加 [`ReactDOM.createRoot()`](https://react.dev/reference/react-dom/client/createRoot) 方法以定位特定的 DOM 元素并创建一个用于显示 React 组件的根节点。然后，添加 [`root.render()`](https://react.dev/reference/react-dom/client/hydrateRoot#root-render) 方法将您的 React 代码渲染到 DOM 中。

<!-- This will tell React to render our `<h1>` title inside our `#app` element. -->

这将告诉 React 在 `#app` 元素内渲染我们的 `<h1>` 标题。

```html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script>
      const app = document.getElementById('app');
      const root = ReactDOM.createRoot(app);
      root.render(<h1>Develop. Preview. Ship.</h1>);
    </script>
  </body>
</html>
```

<!-- If you try to run this code in the browser, you will get a syntax error: -->

如果您尝试在浏览器中运行这段代码，会出现语法错误：

```html
Uncaught SyntaxError: expected expression, got '<'
```

<!-- This is because `<h1>...</h1>` is not valid Javascript. This piece of code is **JSX**. -->

这是因为 `<h1>...</h1>` 不是合法的 JavaScript。这段代码是 **JSX**。

<!-- ## What is JSX? -->

## 什么是 JSX？

<!-- JSX is a syntax extension for JavaScript that allows you to describe your UI in a familiar *HTML-like* syntax. The nice thing about JSX is that apart from following [three JSX rules](https://react.dev/learn/writing-markup-with-jsx#the-rules-of-jsx), you don't need to learn any new symbols or syntax outside of HTML and JavaScript. -->

JSX 是一种 JavaScript 语法扩展，让您可以使用类似 *HTML* 的语法来描述 UI。JSX 的好处是，除了遵循 [三个 JSX 规则](https://react.dev/learn/writing-markup-with-jsx#the-rules-of-jsx)，您无需在 HTML 和 JavaScript 之外学习任何新的符号或语法。

<!-- But browsers don't understand JSX out of the box, so you'll need a JavaScript compiler, such as a [Babel](https://babeljs.io/), to transform your JSX code into regular JavaScript. -->

但是浏览器并不能原生理解 JSX，因此您需要 JavaScript 编译器（例如 [Babel](https://babeljs.io/)）来将 JSX 代码转换成常规 JavaScript。

<!-- ## Adding Babel to your project -->

## 将 Babel 添加到您的项目中

<!-- To add Babel to your project, copy and paste the following script in your `index.html` file: -->

要将 Babel 添加到项目中，请将以下脚本复制并粘贴到 `index.html` 文件中：

```html
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
```

<!-- In addition, you will need to inform Babel what code to transform by changing the script type to `type=text/jsx`. -->

此外，您需要通过将脚本类型更改为 `type=text/jsx` 来告知 Babel 要转换哪些代码。

```html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <!-- Babel Script -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/jsx">
      const domNode = document.getElementById('app');
      const root = ReactDOM.createRoot(domNode);
      root.render(<h1>Develop. Preview. Ship.</h1>);
    </script>
  </body>
</html>
```

<!-- To confirm it's working correctly, open your HTML file in the browser. -->

为了确认其正确运行，请在浏览器中打开您的 HTML 文件。

<!-- Comparing the **declarative** React code you just wrote: -->

看看您刚刚编写的 **声明式** React 代码：

```html
<script type="text/jsx">
  const domNode = document.getElementById("app")
  const root = ReactDOM.createRoot(domNode);
  root.render(<h1>Develop. Preview. Ship.</h1>);
</script>
```

<!-- to the **imperative** JavaScript code you wrote in the previous section: -->

将它和您在上一节中编写的 **命令式** JavaScript 代码比较一下：

```html
<script type="text/javascript">
  const app = document.getElementById('app');
  const header = document.createElement('h1');
  const text = 'Develop. Preview. Ship.';
  const headerContent = document.createTextNode(text);
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
```

<!-- You can start to see how using React enables you to cut down a lot of repetitive code. -->

您可以看到，使用 React 如何帮助您减少大量重复代码。

<!-- And this is exactly what React does, it's a library that contains reusable snippets of code that perform tasks on your behalf - in this case, updating the UI. -->

这正是 React 所做的事情，它是一个包含可重用代码片段的库，代表您执行任务——在本例中是更新 UI。

<!--
> **Additional Resources:**
> 
> You don't need to know exactly how React updates the UI to start using it, but if you'd like to learn more, here are some additional resources:
> 
> - [UI trees](https://react.dev/learn/understanding-your-ui-as-a-tree)
> - [Writing markup with JSX](https://react.dev/learn/writing-markup-with-jsx)
> - [react-dom/server](https://react.dev/reference/react-dom/server) sections in the React Documentation.
-->

> **附加资源：**
>
> 您不需要确切了解 React 如何更新 UI 就可以开始使用它，但如果您想了解更多，这里有一些额外的资源：
>
> - [UI 树](https://react.dev/learn/understanding-your-ui-as-a-tree)
> - [使用 JSX 编写标记](https://react.dev/learn/writing-markup-with-jsx)
> - React 官方文档中的 [react-dom/server](https://react.dev/reference/react-dom/server) 部分。

<!-- ## Essential JavaScript for React -->

## React 的 JavaScript 基础

<!-- While you can learn JavaScript and React at the same time, being familiar with JavaScript can make the process of learning React easier. -->

虽然您可以同时学习 JavaScript 和 React，但熟悉 JavaScript 会让学习 React 的过程更轻松。

<!-- In the next sections, you will be introduced to some core concepts of React from a JavaScript perspective. Here's a summary of the JavaScript topics that will be mentioned: -->

在接下来的章节中，您将从 JavaScript 的角度了解一些 React 的核心概念。以下是将会提到的 JavaScript 主题摘要：

<!--
- [Functions](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions) and [Arrow Functions](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- [Objects](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
- [Arrays and array methods](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [Destructuring](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- [Template literals](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals)
- [Ternary Operators](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)
- [ES Modules and Import / Export Syntax](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Modules)
-->

- [函数](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions) 和 [箭头函数](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- [对象](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
- [数组及其方法](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [解构赋值](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- [模板字符串](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals)
- [三元运算符](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)
- [ES 模块和导入/导出语法](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Modules)

<!-- While this course does not dive into JavaScript, it's good practice to stay up to date with the latest versions of JavaScript. But if you don't feel proficient in JavaScript yet, don't let this hinder you from starting to build with React! -->

虽然本课程并不会深入探讨 JavaScript，但保持对 JavaScript 最新版本的了解是一种好习惯。不过，如果您觉得自己对 JavaScript 还不够熟练，也不要因此阻碍您开始使用 React 进行构建！

<!-- ### It’s time to take a quiz! -->

### 是时候做个测试了！

<!-- Test your knowledge and see what you’ve just learned. -->

测试您的知识，看看您刚刚学到了什么。

<!-- Why do you need to compile your React code? -->

为什么需要编译您的 React 代码？

<!--
A. React uses a new version of HTML that's too advanced for current browsers.

B. React uses JSX which needs to be compiled into JavaScript.

C. React doesn't know how to update the DOM so it needs a compiler to do it.
-->

A. React 使用了一个对当前浏览器来说过于先进的 HTML 新版本。

B. React 使用 JSX，它需要被编译成 JavaScript。

C. React 不知道如何更新 DOM，因此需要编译器来完成。

<!-- JSX is a syntax extension for JavaScript, but browsers don't understand JSX out of the box, so you'll need a JavaScript compiler to transform your JSX code into regular JavaScript. -->

<details>
  <summary>正确答案</summary>
  B。JSX 是 JavaScript 的语法扩展，但浏览器默认不支持 JSX，因此您需要一个 JavaScript 编译器将您的 JSX 代码转换为常规 JavaScript。
</details>
