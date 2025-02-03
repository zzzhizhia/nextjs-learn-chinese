# 第五章 使用组件构建 UI

<!-- ## React core concepts -->

## React 核心概念

<!-- There are three core concepts of React that you'll need to be familiar with to start building React applications. These are: -->

在开始构建 React 应用时，你需要熟悉 React 的三个核心概念。它们是：

<!--
- Components
- Props
- State
-->

- 组件
- 属性（Props）
- 状态（State）

<!-- In the next chapters, we will go through these concepts and provide resources where you can continue learning them. After you're familiar with these concepts, we'll then show you how to install Next.js and use newer React features such as Server and Client Components. -->

在接下来的章节中，我们会介绍这些概念，并提供继续学习所需的资源。在熟悉了这些概念之后，我们会教你如何安装 Next.js，并使用 React 的新特性，如服务端和客户端组件。

<!-- ## Components -->

## 组件

<!-- User interfaces can be broken down into smaller building blocks called **components**. -->

用户界面可以被分解成更小的构建块，这些构建块称为**组件**。

<!-- Components allow you to build self-contained, reusable snippets of code. If you think of components as **LEGO bricks**, you can take these individual bricks and combine them together to form larger structures. If you need to update a piece of the UI, you can update the specific component or brick. -->

组件可以让你构建独立的、可复用的代码片段。把组件想象成**乐高积木**：你可以将这些单独的积木组合起来形成更大的结构。如果你需要更新某个 UI 部分，你可以更新相应的组件或积木。

![一个由图片、文本和按钮等 3 个更小组件组成的媒体组件示例](https://nextjs.org/_next/image?url=%2Flearn%2Flight%2Flearn-components.png&w=3840&q=75)

<!-- This modularity allows your code to be more maintainable as it grows because you can add, update, and delete components without touching the rest of our application. -->

这种模块化让你的代码在规模扩大时更易维护，因为你可以在不触及应用其他部分的情况下添加、更新或删除组件。

<!-- The nice thing about React components is that they are just JavaScript. Let's see how you can write a React component, from a JavaScript perspective: -->

React 组件的好处在于它们只是 JavaScript。让我们从 JavaScript 的角度看看如何编写一个 React 组件：

<!-- ### Creating components -->

### 创建组件

<!-- In React, components are **functions.** Inside your `script` tag, create a new function called `header`: -->

在 React 中，组件就是**函数**。在你的 `script` 标签内，新建一个名为 `header` 的函数：

```html
<script type="text/jsx">
  const app = document.getElementById("app")
 
  function header() {
  }
 
  const root = ReactDOM.createRoot(app);
  root.render(<h1>Develop. Preview. Ship.</h1>);
</script>
```

<!-- A component is a function that **returns UI elements**. Inside the return statement of the function, you can write JSX: -->

组件是一个**返回 UI 元素**的函数。在函数的 return 语句中，你可以编写 JSX：

```html
<script type="text/jsx">
  const app = document.getElementById("app")
 
  function header() {
     return (<h1>Develop. Preview. Ship.</h1>)
   }
 
  const root = ReactDOM.createRoot(app);
  root.render(<h1>Develop. Preview. Ship.</h1>);
</script>
```

<!-- To render this component to the DOM, pass it as the first argument in the `root.render()` method: -->

要将此组件渲染到 DOM 中，将其作为 `root.render()` 方法的第一个参数传递：

```html
<script type="text/jsx">
  const app = document.getElementById("app")
 
  function header() {
     return (<h1>Develop. Preview. Ship.</h1>)
   }
 
  const root = ReactDOM.createRoot(app);
  root.render(header);
</script>
```

<!-- But, wait a second. If you try to run the code above in your browser, you'll get an error. To get this to work, there are two things you have to do: -->

但是，等一下。如果你尝试在浏览器中运行上述代码，你会遇到错误。要使其正常工作，你需要做两件事：

<!-- First, React components should be capitalized to distinguish them from plain HTML and JavaScript: -->

首先，React 组件应该大写，以便与普通的 HTML 和 JavaScript 区分开来：

```html
function Header() {
  return <h1>Develop. Preview. Ship.</h1>;
}
 
const root = ReactDOM.createRoot(app);
// Capitalize the React Component
root.render(Header);
```

<!-- Second, you use React components the same way you'd use regular HTML tags, with angle brackets `<>`: -->

其次，你使用 React 组件的方式与使用普通 HTML 标签相同，使用尖括号 `<>`：

```html
function Header() {
  return <h1>Develop. Preview. Ship.</h1>;
}
 
const root = ReactDOM.createRoot(app);
root.render(<Header />);
```

<!-- If you try to run the code in your browser again, you'll see your changes. -->

如果你再次尝试在浏览器中运行代码，你会看到你的更改。

<!-- ### Nesting components -->

### 嵌套组件

<!-- Applications usually include more content than a single component. You can **nest** React components inside each other like you would regular HTML elements. -->

应用程序通常包含比单个组件更多的内容。你可以像嵌套普通 HTML 元素一样**嵌套** React 组件。

<!-- In your example, create a new component called `HomePage`: -->

在你的示例中，创建一个名为 `HomePage` 的新组件：

```html
function Header() {
  return <h1>Develop. Preview. Ship.</h1>;
}
 
function HomePage() {
  return <div></div>;
}
 
const root = ReactDOM.createRoot(app);
root.render(<Header />);
```

<!-- Then nest the `<Header>` component inside the new `<HomePage>`component: -->

然后将 `<Header>` 组件嵌套在新的 `<HomePage>` 组件中：

```html
function Header() {
  return <h1>Develop. Preview. Ship.</h1>;
}
 
function HomePage() {
  return (
    <div>
      {/* Nesting the Header component */}
      <Header />
    </div>
  );
}
 
const root = ReactDOM.createRoot(app);
root.render(<Header />);
```

<!-- ### Component trees -->

### 组件树

<!-- You can keep nesting React components this way to form component trees. -->

你可以通过这种方式继续嵌套 React 组件，以形成组件树。

![组件树展示了组件如何相互嵌套](https://nextjs.org/_next/image?url=%2Flearn%2Flight%2Flearn-component-tree.png&w=3840&q=75)

<!-- For example, your top-level `HomePage` component could hold a `Header`, an `Article`, and a `Footer` Component. And each of those components could in turn have their own child components and so on. For example, the `Header` component could contain a `Logo`, `Title` and `Navigation` component. -->

例如，你的顶级 `HomePage` 组件可以包含一个 `Header`、一个 `Article` 和一个 `Footer` 组件。而这些组件中的每一个又可以包含它们自己的子组件，依此类推。例如，`Header` 组件可以包含一个 `Logo`、`Title` 和 `Navigation` 组件。

<!-- This modular format allows you to reuse components in different places inside your app. -->

这种模块化格式允许你在应用程序的不同地方重用组件。

<!-- In your project, since `<HomePage>` is now your top-level component, you can pass it to the `root.render()` method: -->

在你的项目中，由于 `<HomePage>` 现在是你的顶级组件，你可以将其传递给 `root.render()` 方法：

```html
function Header() {
  return <h1>Develop. Preview. Ship.</h1>;
}
 
function HomePage() {
  return (
    <div>
      <Header />
    </div>
  );
}
 
const root = ReactDOM.createRoot(app);
root.render(<HomePage />);
```

<!--
> **Additional Resources:**
> 
> - [Your first component](https://react.dev/learn/your-first-component)
> - [Importing and exporting components](https://react.dev/learn/importing-and-exporting-components)
-->

> **附加资源:**
>
> - [你的第一个组件](https://react.dev/learn/your-first-component)
> - [导入和导出组件](https://react.dev/learn/importing-and-exporting-components)

<!-- ### It’s time to take a quiz! -->

### 是时候做个小测验了！

<!-- Test your knowledge and see what you’ve just learned. -->

测试你的知识，看看你刚刚学到了什么。

<!-- How would you nest a \`Nav\` component inside a \`Layout\` component in React? -->

你会如何在 React 中将 `Nav` 组件嵌套在 `Layout` 组件中？

A. \<Layout />\<Nav />

B. \<Layout>\<Nav />\</Layout>

C. \<layout>\<nav>\<nav/>\<layout/>

<!-- In React, you can nest components inside each other, forming a component tree. -->

<details>
  <summary>正确答案</summary>
  B。在 React 中，你可以将组件相互嵌套，形成组件树。
</details>
