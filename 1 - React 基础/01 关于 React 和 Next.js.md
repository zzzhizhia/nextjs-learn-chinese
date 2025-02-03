# 第一章 关于 React 和 Next.js

<!-- Next.js is a flexible **React framework** that gives you building blocks to create fast, full-stack **web applications**. -->

Next.js 是一个灵活的 **React 框架**，它为您提供构建块来创建快速、全栈的 **Web 应用程序**。

<!-- But what exactly do we mean by this? Let's spend some time expanding on what React and Next.js are and how they can help you build web applications. -->

但是这到底是什么意思呢？让我们花一些时间展开来讲讲什么是 React 和 Next.js，以及它们如何帮助您构建 Web 应用程序。

<!-- ### Building blocks of a web application -->

### Web 应用程序的构建块

<!-- There are a few things you need to consider when building modern applications. Such as: -->

当构建现代应用程序的时候，您需要考虑以下这些事情：

<!--
- **User Interface** - how users will consume and interact with your application.
- **Routing** - how users navigate between different parts of your application.
- **Data Fetching** - where your data lives and how to get it.
- **Rendering** - when and where you render static or dynamic content.
- **Integrations** - what third-party services you use (for CMS, auth, payments, etc.) and how you connect to them.
- **Infrastructure** - where you deploy, store, and run your application code (serverless, CDN, edge, etc.).
- **Performance** - how to optimize your application for end-users.
- **Scalability** - how your application adapts as your team, data, and traffic grow.
- **Developer Experience** - your team's experience building and maintaining your application.
-->

- **用户界面** - 用户将如何使用并与您的应用程序交互。
- **路由** - 用户如何在应用程序的不同部分之间导航。
- **数据获取** - 您的数据在何处运作以及如何获取数据。
- **渲染** - 何时何地呈现静态或动态内容。
- **集成** - 您使用哪些第三方服务（用于 CMS、AUTH、付款等），以及如何连接它们。
- **基础架构** - 部署，存储和运行应用程序代码（serverless，CDN，Edge 等）的位置。
- **性能** - 如何优化终端用户的应用程序。
- **可扩展性** - 您的应用程序如何适应团队、数据和流量的增长。
- **开发人员经验** - 团队的经验建立和维护您的应用程序。

<!-- For each part of your application, you will need to decide whether you will build a solution yourself or use other tools, such as packages, libraries, and frameworks. -->

对于应用程序的每个部分，您将需要决定是自己构建解决方案还是借助其他工具，例如软件包、库和框架。

<!-- ### What is React? -->

### 什么是 React？

<!-- [React](https://react.dev/) is a JavaScript **library** for building **interactive user interfaces**. -->

[React](https://react.dev/) 是一个用于构建 **交互式用户界面** 的 JavaScript **库**。

<!-- By user interfaces (UI), we mean the elements that users see and interact with on-screen. -->

用户界面（UI）是指用户在屏幕上看到并与之交互的元素。

![User Interface example showing a browser window with a navigation, a sidebar, and a list of posts](https://nextjs.org/_next/image?url=%2Flearn%2Flight%2Flearn-react-components.png&w=3840&q=75)

<!-- By library, we mean React provides helpful functions (APIs) to build UI, but leaves it up to the developer where to use those functions in their application. -->

我们所说的库是指 React 提供有用的函数（API）来构建 UI，但这些函数在应用程序的何处使用由开发者决定。

<!-- Part of React's success is that it is relatively unopinionated about the other aspects of building applications. This has resulted in a flourishing ecosystem of third-party tools and solutions, including Next.js. -->

React 的成功部分在于它在构建应用程序的其他方面相对中立。这使得一个繁荣的第三方工具和解决方案生态系统发展起来，其中包括 Next.js。

<!-- It also means, however, that building a complete React application from the ground up requires some effort. Developers need to spend time configuring tools and reinventing solutions for common application requirements. -->

然而，这也代表从头开始构建一个完整的 React 应用程序需要一些努力。

<!-- ## What is Next.js? -->

## 什么是 Next.js？

<!-- Next.js is a React **framework** that gives you building blocks to create web applications. -->

Next.js 是一个提供构建块用于创建 Web 应用程序的 React **框架**。

<!-- By framework, we mean Next.js handles the tooling and configuration needed for React, and provides additional structure, features, and optimizations for your application. -->

框架是指 Next.js 处理 React 所需的工具和配置，并为您的应用程序提供额外的结构、功能和优化。

![Diagram showing how Next.js spans the server and client, and provides additional features such as routing, data fetching, and rendering.](https://nextjs.org/_next/image?url=%2Flearn%2Flight%2Flearn-ecosystem.png&w=3840&q=75)

<!-- You can use React to build your UI, then incrementally adopt Next.js features to solve common application requirements such as routing, data fetching, and caching - all while improving the developer and end-user experience. -->

您可以使用 React 构建您的 UI，然后逐步利用 Next.js 功能来解决常见应用需求，如路由、数据获取和缓存，同时提升开发者和终端用户的使用体验。

<!-- Whether you're an individual developer or part of a larger team, you can use React and Next.js to build fully interactive, highly dynamic, and performant web applications. -->

无论您是个人开发者还是大型团队的一员，您都可以使用 React 和 Next.js 构建完全交互、高度动态和性能卓越的 Web 应用程序。

<!-- In the next chapters, we will discuss how you can get started with React and Next.js. -->

在下一章中，我们将讨论如何开始使用 React 和 Next.js。
