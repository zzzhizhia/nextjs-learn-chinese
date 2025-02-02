# 第三章 使用 JavaScript 更新 UI

<!-- In this chapter, we'll start building out our project by using JavaScript and DOM methods to add an `h1` tag to your project. -->

在本章中，我们将开始使用 JavaScript 和 DOM 方法为您的项目添加一个 `h1` 标签，从而开始构建我们的项目。

<!-- Open your code editor and create a new `index.html` file. Inside the HTML file, add the following code: -->

打开您的代码编辑器并创建一个新的 `index.html` 文件。在 HTML 文件中，添加以下代码：

```html
<html>
  <body>
    <div></div>
  </body>
</html>
```

<!-- Then give the `div` a unique `id` so that you can target it later. -->

然后给 `div` 一个独特的 `id`，以便您之后可以定位它。

```html
<html>
  <body>
    <div id="app"></div>
  </body>
</html>
```

<!-- To write JavaScript inside your HTML file, add a `script` tag: -->

要在您的 HTML 文件中编写 JavaScript，请添加一个 `script` 标签：

```html
<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript"></script>
  </body>
</html>
```

<!-- Now, inside the `script` tag, you can use a DOM method, [`getElementById()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById), to select the `<div>` element by its `id`: -->

现在，在这个 `script` 标签内，您可以使用 DOM 方法 [`getElementById()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)，通过它的 `id` 选择 `<div>` 元素：

```html
<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript">
      const app = document.getElementById('app');
    </script>
  </body>
</html>
```

<!-- You can continue using DOM methods to create a new `<h1>` element: -->

您可以继续使用 DOM 方法来创建一个新的 `<h1>` 元素：

```html
<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript">
      // Select the div element with 'app' id
      const app = document.getElementById('app');
 
      // Create a new H1 element
      const header = document.createElement('h1');
 
      // Create a new text node for the H1 element
      const text = 'Develop. Preview. Ship.';
      const headerContent = document.createTextNode(text);
 
      // Append the text to the H1 element
      header.appendChild(headerContent);
 
      // Place the H1 element inside the div
      app.appendChild(header);
    </script>
  </body>
</html>
```

<!-- To make sure everything is working, open your HTML file inside your browser of choice. You should see an `h1` tag that says, 'Develop. Preview. Ship.'. -->

为了确保一切正常，请在您选择的浏览器中打开您的 HTML 文件。您应该看到一个 `h1` 标签，上面写着 'Develop. Preview. Ship.'。

## HTML vs. the DOM

<!-- If you look at the DOM elements inside your [browser developer tools](https://developer.mozilla.org/docs/Learn/Common_questions/Tools_and_setup/What_are_browser_developer_tools), you will notice the DOM includes the `<h1>` element. The DOM of the page is different from the source code - or in other words, the original HTML file you created. -->

如果您查看 [浏览器开发者工具](https://developer.mozilla.org/docs/Learn/Common_questions/Tools_and_setup/What_are_browser_developer_tools) 中的 DOM 元素，您会注意到 DOM 包含 `<h1>` 元素。页面的 DOM 与源代码不同 - 换句话说，与您创建的原始 HTML 文件不同。

![Two side-by-side diagrams showing the differences between the rendered DOM elements and Source Code (HTML)](https://nextjs.org/_next/image?url=%2Flearn%2Flight%2Flearn-dom-and-source.png&w=3840&q=75)

<!-- This is because the HTML represents the **initial page content**, whereas the DOM represents the **updated page content** which was changed by the JavaScript code you wrote. -->

这是因为 HTML 代表 **初始页面内容**，而 DOM 代表 **更新后的页面内容**，这些内容是由您编写的 JavaScript 代码更改的。

<!-- Updating the DOM with plain JavaScript is very powerful but verbose. You've written all this code to add an `<h1>` element with some text: -->

使用纯 JavaScript 更新 DOM 非常强大但冗长。您已经编写了所有这些代码来添加一个带有一些文本的 `<h1>` 元素：

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

<!-- As the size of an app or team grows, it can become increasingly challenging to build applications this way. -->

随着应用程序或团队规模的增长，以这种方式构建应用程序可能会变得越来越具有挑战性。

<!-- With this approach, developers spend a lot of time writing instructions to tell the computer **how** it should do things. But wouldn't it be nice to describe **what** you want to show and let the computer figure out **how** to update the DOM? -->

使用这种方法，开发人员花费大量时间编写指令来告诉计算机 **如何** 执行操作。但是，描述您想要显示的内容并让计算机找出 **如何** 更新 DOM 不是更好吗？

<!-- ## Imperative vs. declarative programming -->

## 命令式 vs. 声明式编程

<!-- The code above is a good example of **imperative** **programming.** You're writing the steps for **how** the user interface should be updated. But when it comes to building user interfaces, a declarative approach is often preferred because it can speed up the development process. Instead of having to write DOM methods, it would be helpful if developers were able to declare **what** they want to show (in this case, an `h1` tag with some text). -->

上面的代码是 **命令式编程** 的一个很好的例子。您正在编写 **如何** 更新用户界面的步骤。但是在构建用户界面时，通常更喜欢声明式方法，因为它可以加快开发过程。如果开发人员能够声明他们想要显示的内容（在本例中是一个带有一些文本的 `h1` 标签），而不是必须编写 DOM 方法，那将是有帮助的。

<!-- In other words, **imperative programming** is like giving a chef step-by-step instructions on how to make a pizza. **Declarative programming** is like ordering a pizza without being concerned about the steps it takes to make the pizza. 🍕 -->

换句话说，**命令式编程** 就像给厨师提供制作披萨的分步说明。**声明式编程** 就像点披萨而不关心制作披萨的步骤。🍕

<!-- [React](https://react.dev/) is a popular declarative library that you can use build user interfaces. -->

[React](https://react.dev/) 是一个流行的声明式库，您可以使用它来构建用户界面。


<!-- ## React: A declarative UI library -->

## React：一个声明式 UI 库

<!-- As a developer, you can tell React what you want to happen to the user interface, and React will figure out the steps of **how** to update the DOM on your behalf. -->

作为开发人员，您可以告诉 React 您希望用户界面发生什么，React 将代表您找出 **如何** 更新 DOM 的步骤。

<!-- In the next section, we'll explore how you can get started with React. -->

在下一节中，我们将探讨如何开始使用 React。

<!-- ### It’s time to take a quiz! -->

### 是时候做个测试了！

<!-- Test your knowledge and see what you’ve just learned. -->

测试您的知识，看看您刚刚学到了什么。

<!-- Which of the following statements is more declarative? -->

以下哪种说法更具声明性？

<!-- A. "Knead the dough, roll the dough, add tomato sauce, add cheese, add ham, add pineapple, bake at 200 degrees celsius in a stone oven for..." -->

A. “揉面团，擀面团，加番茄酱，加奶酪，加火腿，加菠萝，在石炉中以 200 摄氏度烘烤……”

<!-- "A Hawaiian pizza please." -->

B. “请来一份夏威夷披萨。”

<!-- Declarative programming allows you to describe what you want to happen, rather than the steps to make it happen. -->

<details>
  <summary>正确答案</summary>
  B。声明式编程允许您描述您想要发生的事情，而不是实现它的步骤。
</details>

<!--
> **Additional Resources:**
> 
> - [HTML vs. the DOM](https://developer.chrome.com/docs/devtools/dom/#appendix)
> - [How declarative UI compares to imperative](https://react.dev/learn/reacting-to-input-with-state#how-declarative-ui-compares-to-imperative)
-->

> **附加资源：**
>
> - [HTML vs. the DOM](https://developer.chrome.com/docs/devtools/dom/#appendix)
> - [How declarative UI compares to imperative](https://react.dev/learn/reacting-to-input-with-state#how-declarative-ui-compares-to-imperative)
