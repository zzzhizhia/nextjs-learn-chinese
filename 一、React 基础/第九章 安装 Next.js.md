<!-- # Installing Next.js -->

# 第九章 安装 Next.js

<!-- When you use Next.js in your project, you do not need to load the `react` and `react-dom` scripts from [unpkg.com](http://unpkg.com/) anymore. Instead, you can install these packages locally using `npm` or your preferred package manager. -->

当你在项目中使用 Next.js 时，你无需再从 [unpkg.com](http://unpkg.com/) 加载 `react` 和 `react-dom` 脚本。相反，你可以使用 `npm` 或你偏好的包管理器在本地安装这些包。

<!-- > **Note**: To use Next.js, you will need to have Node.js version **18.17.0** or above installed on your machine ([see minimum version requirement](https://nextjs.org/docs/getting-started/installation)), you can [download it here](https://nodejs.org/en/). -->

> **注意**：要使用 Next.js，你需要在你的机器上安装 Node.js 版本 **18.17.0** 或更高（[查看最低版本要求](https://nextjs.org/docs/getting-started/installation)），你可以在[这里](https://nodejs.org/en/)下载。

<!-- To do so, create a new file in the same directory as your `index.html` file, called `package.json` with an empty object `{}`. -->

要实现这一点，请在与你的 `index.html` 文件相同的目录下创建一个名为 `package.json` 的新文件，并在其中放置一个空对象 `{}`。

```json
{}
```

<!-- In your [terminal](https://code.visualstudio.com/docs/terminal/basics), run the following command in the root of your project: -->

在你的 [终端](https://code.visualstudio.com/docs/terminal/basics) 中，在项目根目录下运行以下命令：

```shell
npm install react@latest react-dom@latest next@latest
```

<!-- Once the installation is complete, you should be able to see your project dependencies listed inside your `package.json` file: -->

安装完成后，你应该可以在 `package.json` 文件中看到项目依赖列表：

```json
{
  "dependencies": {
    "next": "^14.0.3",
    "react": "^18.3.1",
    "react-dom": "^18.3.1"
  }
}
```

<!-- Don't worry if you're on later versions than the ones shown above, as long as you have the `next`, `react`, and `react-dom` packages installed, you're good to go. -->

如果版本比上面展示的版本更新也不用担心，只要你安装了 `next`、`react` 和 `react-dom` 包就可以了。

<!-- You will also notice a new file called `package-lock.json` file that contains detailed information about the exact versions of each package. -->

你还会发现生成了一个名为 `package-lock.json` 的新文件，它包含有关每个包确切版本的详细信息。

<!-- Jumping back to the `index.html` file, you can delete the following code: -->

回到 `index.html` 文件，你可以删除以下代码：

<!-- 1. The `<html>` and `<body>` tags.  
2. The `<div>` element with the `id` of `app`.  
3. The `react` and `react-dom` scripts since you've installed them with NPM.  
4. The `Babel` script because Next.js has a compiler that transforms JSX into valid JavaScript browsers can understand.  
5. The `<script type="text/jsx">` tag.  
6. The `document.getElementById()` and `ReactDom.createRoot()` methods.  
7. The `React.` part of the `React.useState(0)` function -->

1. `<html>` 和 `<body>` 标签  
2. 带有 `id` 为 `app` 的 `<div>` 元素  
3. 已通过 NPM 安装的 `react` 和 `react-dom` 脚本  
4. `Babel` 脚本，因为 Next.js 自带编译器来将 JSX 转换为浏览器可理解的 JavaScript  
5. `<script type="text/jsx">` 标签  
6. `document.getElementById()` 和 `ReactDom.createRoot()` 方法  
7. `React.useState(0)` 中的 `React.` 部分

<!-- After deleting the lines above, add the following import to the top of your file: -->

删除上述代码后，在文件顶部添加如下导入：

```html
import { useState } from 'react';
```

<!-- Your code should look like this: -->

你的代码应如下所示：

```html
import { useState } from 'react';
 
function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
}
 
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];
 
  const [likes, setLikes] = useState(0);
 
  function handleClick() {
    setLikes(likes + 1);
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
  );
}
```

<!-- The only code left in the HTML file is JSX, so you can change the file type from `.html` to `.js` or `.jsx`. -->

目前 HTML 文件中只剩下 JSX，因此你可以将该文件从 `.html` 更改为 `.js` 或 `.jsx`。

<!-- ## Creating your first page -->

## 创建你的第一个页面

<!-- Next.js uses file-system routing. This means that instead of using code to define the routes of your application, you can use folders and files. -->

Next.js 使用文件系统路由。这意味着你无需使用代码来定义应用程序的路由，只需使用文件夹和文件即可。

<!-- Here's how you can create your first page in Next.js: -->

以下是在 Next.js 中创建第一个页面的方法：

<!-- 1. Create a new folder called [app](https://nextjs.org/docs/app/building-your-application/routing#the-app-router) and move the `index.js` file inside it.  
2. Rename your `index.js` file to `page.js`. This will be the main page of your application.  
3. Add `export default` to your `<HomePage>` component to help Next.js distinguish which component to render as the main component of the page. -->

1. 创建一个名为 [app](https://nextjs.org/docs/app/building-your-application/routing#the-app-router) 的新文件夹，并将 `index.js` 文件移动到其中。  
2. 将 `index.js` 文件重命名为 `page.js`。它将成为应用程序的主页面。  
3. 在 `<HomePage>` 组件前添加 `export default`，以便 Next.js 知道要将哪个组件作为页面的主要组件进行渲染。

```js
import { useState } from 'react';
 
function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
}
 
export default function HomePage() {
  // ...
}
```

<!-- ## Running the development server -->

## 运行开发服务器

<!-- Next, let's run your development server so you can see the changes in your new page while developing. Add a `"next dev"` script to your `package.json` file: -->

接下来，让我们运行开发服务器，以便你在开发时能够看到新页面的变化。在 `package.json` 文件中添加一个 `"next dev"` 脚本：

```json
{
  "scripts": {
    "dev": "next dev"
  },
  "dependencies": {
    "next": "^14.0.3",
    "react": "^18.3.1",
    "react-dom": "^18.3.1"
  }
}
```

<!-- Check what happens by running `npm run dev` in your terminal. You'll notice two things: -->

在终端中运行 `npm run dev`，你会注意到两件事：

<!-- 1. When you navigate to [localhost:3000](http://localhost:3000/), you should see the following error: -->

1. 当你访问 [localhost:3000](http://localhost:3000/) 时，你会看到如下错误：

![Next.js Error Message: You're importing a component that needs useState. It only works in a Client component...](https://nextjs.org/_next/image?url=%2Flearn%2Flight%2Flearn-usestate-rsc-error.png&w=3840&q=75)

<!-- This is because Next.js uses React Server Components, a new feature that allows React to render on the server. Server Components don't support `useState`, so you'll need to use a Client Component instead. -->

这是因为 Next.js 使用了 React Server Components，一种允许 React 在服务器端渲染的新特性。服务器组件不支持 `useState`，因此你需要改用客户端组件。

<!-- In the next chapter, we'll discuss the main differences between Server and Client Components and fix this error. -->

在下一章中，我们将讨论服务器组件与客户端组件之间的主要区别，并修复该错误。

<!-- 2. A new file called `layout.js` was automatically created inside the `app` folder. This is the main layout of your application. You can use it to add UI elements that are shared across all pages (e.g. navigation, footer, etc). -->

2. 在 `app` 文件夹中自动生成了一个名为 `layout.js` 的新文件。它是你应用程序的主要布局，你可以用它来添加跨所有页面共享的 UI 元素（如导航、页脚等）。

```js
export const metadata = {
  title: 'Next.js',
  description: 'Generated by Next.js',
};
 
export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```

<!-- ## Summary -->

## 总结

<!-- Looking at the migration so far, you may already be getting a sense of the benefits of using Next.js:

- You removed the React and Babel scripts; a taste of the complex tooling and configuration you no longer have to think about.
- You created your first page. -->

通过目前的迁移，你或许已经感受到了使用 Next.js 的一些好处：

- 你移除了 React 和 Babel 脚本，避免了复杂的工具和配置。  
- 你创建了第一个页面。

<!-- > **Additional Reading:**  
>  
> - [Next.js Routing Fundamentals](https://nextjs.org/docs/app/building-your-application/routing)  
> - [Defining Routes](https://nextjs.org/docs/app/building-your-application/routing/defining-routes)  
> - [Pages and Layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts) -->

> **更多阅读：**  
>  
> - [Next.js 路由基础](https://nextjs.org/docs/app/building-your-application/routing)  
> - [定义路由](https://nextjs.org/docs/app/building-your-application/routing/defining-routes)  
> - [页面和布局](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts)
