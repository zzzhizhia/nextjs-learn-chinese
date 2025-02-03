<!-- # From React to Next.js -->

# 第八章 从 React 到 Next.js

<!-- So far, we explored how you can get started with React. This is what the final code looked like. If you're starting from here, paste this code into an `index.html` file in your code editor. -->

到目前为止，我们已经探讨了如何开始使用 React。这就是最终的代码示例。如果你是从这里开始，请将此代码粘贴到你的代码编辑器中的 `index.html` 文件中。

```html
<html>
  <body>
    <div id="app"></div>
 
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
 
    <script type="text/jsx">
      const app = document.getElementById("app")
 
      function Header({ title }) {
        return <h1>{title ? title : "Default title"}</h1>
      }
 
      function HomePage() {
        const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"]
 
        const [likes, setLikes] = React.useState(0)
 
        function handleClick() {
          setLikes(likes + 1)
        }
 
        return (
          <div>
            <Header title="Develop. Preview. Ship." />
            <ul>
              {names.map((name) => (
                <li key={name}>{name}</li>
              ))}
            </ul>
 
            <button onClick={handleClick}>Like ({likes})</button>
          </div>
        )
      }
 
      const root = ReactDOM.createRoot(app);
      root.render(<HomePage />);
    </script>
  </body>
</html>
```

<!-- In the last few chapters, you were introduced to three essential React concepts: **components**, **props**, and **state**. Having a strong foundation in these will help you get started building React applications. -->

在过去的几章中，你已经了解了三个重要的 React 概念：**组件**、**属性**和**状态**。在这些方面打下坚实的基础将帮助你开始构建 React 应用。

<!-- When it comes to learning React, **the best way to learn is to build**. You can gradually adopt React by using `<script>` and what you've learned so far to add small components to an existing website. However, many developers have found the user and developer experience React enables valuable enough to dive right in and write their whole frontend application in React. -->

在学习 React 时，**最好的学习方式就是动手构建**。你可以通过使用 `<script>` 以及到目前为止所学的知识在现有网站中逐步添加小的组件，从而逐步采用 React。然而，许多开发者发现 React 所带来的用户和开发体验非常宝贵，因此他们会直接深入并使用 React 构建整个前端应用。

<!-- ## From React to Next.js -->

## 从 React 到 Next.js

<!-- While React excels at building UI, it does take some work to independently build that UI into a fully functioning scalable application. There are also newer React features, like Server and Client Components, that require a framework. The good news is that Next.js handles much of the setup and configuration and has additional features to help you build React applications. -->

虽然 React 在构建 UI 方面表现出色，但要将 UI 独立构建成一个功能完善、可扩展的应用仍需付出一定的努力。React 还引入了如服务器组件和客户端组件等最新特性，这些特性需要一个框架来支持。好消息是，Next.js 处理了大部分的设置和配置，并提供了额外的功能来帮助你构建 React 应用。

<!-- Next, we'll migrate the example from React to Next.js, discuss how Next.js works, and introduce you to the differences between Server and Client Components. -->

接下来，我们将把示例从 React 迁移到 Next.js，讨论 Next.js 的工作原理，并向你介绍服务器组件和客户端组件之间的区别。
