# 第二章 渲染用户界面（UI）

<!-- To understand how React works, we first need a basic understanding of how browsers interpret your code to create (or render) user interfaces (UI). -->

要理解 React 如何工作，我们首先需要对浏览器如何解释您的代码来创建（或渲染）用户界面 (UI) 有一个基本的了解。

<!-- When a user visits a web page, the server returns an HTML file to the browser that may look like this: -->

当用户访问网页时，服务器会将 HTML 文件返回给浏览器，看起来可能是这样的：

![Two side-by-side diagrams, left showing the HTML code, and right showing the DOM tree.](https://nextjs.org/_next/image?url=%2Flearn%2Flight%2Flearn-html-and-dom.png&w=3840&q=75)

<!-- The browser then reads the HTML and constructs the Document Object Model (DOM). -->

浏览器随后会读取 HTML 并构建文档对象模型 (DOM)。

<!-- ### What is the DOM? -->

### 什么是 DOM？

<!-- The DOM is an object representation of the HTML elements. It acts as a bridge between your code and the user interface, and has a tree-like structure with parent and child relationships. -->

DOM 是对 HTML 元素的对象表示。它充当您的代码与用户界面之间的桥梁，并且具有树状结构，包含父级和子级关系。

![Two side-by-side diagrams, left showing the DOM tree, and right showing the rendered UI.](https://nextjs.org/_next/image?url=%2Flearn%2Flight%2Flearn-dom-and-ui.png&w=3840&q=75)

<!-- You can use DOM methods and JavaScript, to listen to user events and [manipulate the DOM](https://developer.mozilla.org/docs/Learn/JavaScript/Client-side_web_APIs/Manipulating_documents) by selecting, adding, updating, and deleting specific elements in the user interface. DOM manipulation allows you to not only target specific elements, but also change their style and content. -->

您可以使用 DOM 方法和 JavaScript 来监听用户事件并通过选择、添加、更新和删除用户界面中的特定元素来操作 DOM。这不仅能让您定位特定元素，还能更改它们的样式和内容。

<!-- In the next section you'll learn how to use JavaScript and DOM methods. -->

在下一节中，您将学习如何使用 JavaScript 和 DOM 方法。

<!-- 
> **Additional Resources:**
> 
> - [Introduction to the DOM](https://developer.mozilla.org/docs/Web/API/Document_Object_Model/Introduction)
> - [How to view the DOM in Google Chrome](https://developer.chrome.com/docs/devtools/dom/)
> - [How to view the DOM in Firefox](https://developer.mozilla.org/docs/Tools/Debugger/How_to/Highlight_and_inspect_DOM_nodes)
-->

> **附加资源：**
>
> - [DOM 简介](https://developer.mozilla.org/docs/Web/API/Document_Object_Model/Introduction)
> - [如何在 Google Chrome 中查看 DOM](https://developer.chrome.com/docs/devtools/dom/)
> - [如何在 Firefox 中查看 DOM](https://developer.mozilla.org/docs/Tools/Debugger/How_to/Highlight_and_inspect_DOM_nodes)

<!-- ### It’s time to take a quiz! -->

### 现在是时候测试一下了！

<!-- Test your knowledge and see what you’ve just learned. -->

测试一下您的知识，看看刚才学到了什么。

<!-- 
True or False: You can update the page content by manipulating the DOM. 

True. The DOM is an object representation of the HTML elements. It acts as a bridge between your code and the user interface, and has a tree-like structure with parent and child relationships.
-->

判断题：您可以通过操作 DOM 来更新页面内容。

<details>
  <summary>正确答案</summary>
  是。DOM 是 HTML 元素的对象表示形式。它作为您的代码与用户界面之间的桥梁，具有树状结构，包含父级和子级关系。
</details>

<!-- ## You've Completed Chapter 2 -->

## 您已完成第 2 章

<!-- You should now understand the fundamentals of how UI is rendered on the browser. -->

您现在应该了解了在浏览器中渲染 UI 的基础知识。

<!-- Next Up -->

接下来

<!-- 3: Updating UI with Javascript -->

3：使用 JavaScript 更新 UI

<!-- Learn how developers use JavaScript to manipulate the DOM and update the UI. -->

学习开发者如何使用 JavaScript 来操作 DOM 并更新 UI。
