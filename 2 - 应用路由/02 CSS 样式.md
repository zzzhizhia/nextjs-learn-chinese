<!-- # CSS Styling -->

# CSS 样式

<!-- Currently, your home page doesn't have any styles. Let's look at the different ways you can style your Next.js application. -->
目前，您的主页没有任何样式。让我们来看一下您可以为 Next.js 应用添加样式的不同方式。

<!-- In this chapter...
Here are the topics we’ll cover -->
以下是我们在本章中涵盖的主题：

<!--
- How to add a global CSS file to your application.
- Two different ways of styling: Tailwind and CSS modules.
- How to conditionally add class names with the `clsx` utility package.
-->
- 如何为您的应用添加全局 CSS 文件。
- 两种不同的样式方式：Tailwind 和 CSS 模块。
- 如何使用 `clsx` 工具包有条件地添加类名。

<!-- ## Global styles -->
## 全局样式

<!-- If you look inside the `/app/ui` folder, you'll see a file called `global.css`. You can use this file to add CSS rules to **all** the routes in your application - such as CSS reset rules, site-wide styles for HTML elements like links, and more. -->
如果你查看 `/app/ui` 文件夹，会看到一个名为 `global.css` 的文件。你可以使用该文件为应用的**所有**路由添加 CSS 规则 —— 例如 CSS 重置规则、HTML 元素（如链接）的全局样式等。

<!-- You can import `global.css` in any component in your application, but it's usually good practice to add it to your top-level component. In Next.js, this is the [root layout](https://nextjs.org/docs/app/api-reference/file-conventions/layout#root-layouts) (more on this later). -->
你可以在应用中的任一组件中导入 `global.css`，但通常建议将其添加到顶层组件中。在 Next.js 中，这个组件是 [根布局](https://nextjs.org/docs/app/api-reference/file-conventions/layout#root-layouts)（稍后会详细介绍）。

<!-- Add global styles to your application by navigating to `/app/layout.tsx` and importing the `global.css` file: -->
通过导航至 `/app/layout.tsx` 并导入 `global.css` 文件，为你的应用添加全局样式：

```tsx
import '@/app/ui/global.css';
 
export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```

<!-- With the development server still running, save your changes and preview them in the browser. Your home page should now look like this: -->
在开发服务器运行时，保存更改并在浏览器中预览。你的主页现在应如下所示：

![Styled page with the logo 'Acme', a description, and login link.](https://nextjs.org/_next/image?url=%2Flearn%2Flight%2Fhome-page-with-tailwind.png&w=1920&q=75)

<!-- But wait a second, you didn't add any CSS rules, where did the styles come from? -->
但等一下，你没有添加任何 CSS 规则，样式究竟从何而来？

<!-- If you take a look inside `global.css`, you'll notice some `@tailwind` directives: -->
如果你查看 `global.css`，会注意到一些 `@tailwind` 指令：

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## Tailwind

<!-- [Tailwind](https://tailwindcss.com/) is a CSS framework that speeds up the development process by allowing you to quickly write [utility classes](https://tailwindcss.com/docs/utility-first) directly in your React code. -->
[Tailwind](https://tailwindcss.com/) 是一个 CSS 框架，它通过允许你在 React 代码中直接快速编写 [实用类](https://tailwindcss.com/docs/utility-first) 来加速开发过程。

<!-- In Tailwind, you style elements by adding class names. For example, adding `"text-blue-500"` will turn the `<h1>` text blue: -->
在 Tailwind 中，你通过添加类名来为元素设置样式。例如，添加 `"text-blue-500"` 会将 `<h1>` 文本变为蓝色：

```tsx
<h1 className="text-blue-500">I'm blue!</h1>
```

<!-- Although the CSS styles are shared globally, each class is singularly applied to each element. This means if you add or delete an element, you don't have to worry about maintaining separate stylesheets, style collisions, or the size of your CSS bundle growing as your application scales. -->
尽管 CSS 样式是全局共享的，但每个类是单独应用于每个元素的。这意味着如果你添加或删除一个元素，你不必担心维护单独的样式表、样式冲突或随着应用扩展而增加的 CSS 包大小。

<!-- When you use `create-next-app` to start a new project, Next.js will ask if you want to use Tailwind. If you select `yes`, Next.js will automatically install the necessary packages and configure Tailwind in your application. -->
当你使用 `create-next-app` 启动一个新项目时，Next.js 会询问你是否要使用 Tailwind。如果你选择 `yes`，Next.js 会自动安装必要的包并在你的应用中配置 Tailwind。

<!-- If you look at `/app/page.tsx`, you'll see that we're using Tailwind classes in the example. -->
如果你查看 `/app/page.tsx`，你会看到我们在示例中使用了 Tailwind 类。

```tsx
import AcmeLogo from '@/app/ui/acme-logo';
import { ArrowRightIcon } from '@heroicons/react/24/outline';
import Link from 'next/link';
 
export default function Page() {
  return (
    // These are Tailwind classes:
    <main className="flex min-h-screen flex-col p-6">
      <div className="flex h-20 shrink-0 items-end rounded-lg bg-blue-500 p-4 md:h-52">
    // ...
  )
}
```

<!-- Don't worry if this is your first time using Tailwind. To save time, we've already styled all the components you'll be using. -->
如果这是你第一次使用 Tailwind，不用担心。为了节省时间，我们已经为你将要使用的所有组件设置了样式。

<!-- Let's play with Tailwind! Copy the code below and paste it above the `<p>` element in `/app/page.tsx`: -->
让我们来玩一下 Tailwind！复制下面的代码并将其粘贴到 `/app/page.tsx` 中的 `<p>` 元素上方：

```tsx
<div
  className="relative w-0 h-0 border-l-[15px] border-r-[15px] border-b-[26px] border-l-transparent border-r-transparent border-b-black"
/>
```

<!-- ### It’s time to take a quiz! -->

### 是时候做个小测验了！

<!-- Test your knowledge and see what you’ve just learned. -->
测试你的知识，看看你刚刚学到了什么。

<!-- What shape do you see when using the code snippet above? -->
使用上面的代码片段时，你看到了什么形状？

<!--
A. A yellow star
B. A blue triangle
C. A black triangle
D. A red circle
-->
A. 黄色的星形  
B. 蓝色的三角形  
C. 黑色的三角形  
D. 红色的圆形

<!-- The border class names are used to create a triangle shape. -->

<details>
  <summary>正确答案</summary>
  C。这些边框类名用于创建一个三角形。
</details>
<br>

<!-- If you prefer writing traditional CSS rules or keeping your styles separate from your JSX - CSS Modules are a great alternative. -->
如果你更喜欢编写传统的 CSS 规则或将样式与 JSX 分开，CSS 模块是一个很好的选择。

<!-- ## CSS Modules -->

## CSS 模块

<!-- [CSS Modules](https://nextjs.org/docs/basic-features/built-in-css-support) allow you to scope CSS to a component by automatically creating unique class names, so you don't have to worry about style collisions as well. -->
[CSS 模块](https://nextjs.org/docs/basic-features/built-in-css-support) 允许你通过自动创建唯一的类名来将 CSS 限定在组件范围内，因此你也不必担心样式冲突。

<!-- We'll continue using Tailwind in this course, but let's take a moment to see how you can achieve the same results from the quiz above using CSS modules. -->
我们将在本课程中继续使用 Tailwind，但让我们花点时间看看如何使用 CSS 模块实现上面测验中的相同结果。

<!-- Inside `/app/ui`, create a new file called `home.module.css` and add the following CSS rules: -->
在 `/app/ui` 中，创建一个名为 `home.module.css` 的新文件，并添加以下 CSS 规则：

```css
.shape {
  height: 0;
  width: 0;
  border-bottom: 30px solid black;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}
```

<!-- Then, inside your `/app/page.tsx` file import the styles and replace the Tailwind class names from the `<div>` you've added with `styles.shape`: -->
然后，在你的 `/app/page.tsx` 文件中导入样式，并将你添加的 `<div>` 中的 Tailwind 类名替换为 `styles.shape`：

```tsx
import AcmeLogo from '@/app/ui/acme-logo';
import { ArrowRightIcon } from '@heroicons/react/24/outline';
import Link from 'next/link';
import styles from '@/app/ui/home.module.css';
 
export default function Page() {
  return (
    <main className="flex min-h-screen flex-col p-6">
      <div className={styles.shape} />
    // ...
  )
}
```

<!-- Save your changes and preview them in the browser. You should see the same shape as before. -->
保存更改并在浏览器中预览。你应该会看到与之前相同的形状。

<!-- Tailwind and CSS modules are the two most common ways of styling Next.js applications. Whether you use one or the other is a matter of preference - you can even use both in the same application! -->
Tailwind 和 CSS 模块是为 Next.js 应用设置样式的两种最常见方式。使用哪一种取决于个人偏好 —— 你甚至可以在同一个应用中同时使用这两种方式！

<!-- ### It’s time to take a quiz! -->

### 是时候做个小测验了！

<!-- Test your knowledge and see what you’ve just learned. -->
测试你的知识，看看你刚刚学到了什么。

<!-- What is one benefit of using CSS modules? -->
使用 CSS 模块的一个好处是什么？

<!-- ## Using the clsx library to toggle class names -->

## 使用 clsx 库切换类名

<!-- There may be cases where you may need to conditionally style an element based on state or some other condition. -->
在某些情况下，你可能需要根据状态或其他条件有条件地设置元素样式。

<!-- [`clsx`](https://www.npmjs.com/package/clsx) is a library that lets you toggle class names easily. We recommend taking a look at [documentation](https://github.com/lukeed/clsx) for more details, but here's the basic usage: -->
[`clsx`](https://www.npmjs.com/package/clsx) 是一个可以让你轻松切换类名的库。我们建议你查看 [文档](https://github.com/lukeed/clsx) 以了解更多详细信息，但这里是基本用法：

<!-- - Suppose that you want to create an `InvoiceStatus` component which accepts `status`. The status can be `'pending'` or `'paid'`. -->
假设你想创建一个接受 `status` 的 `InvoiceStatus` 组件。状态可以是 `'pending'` 或 `'paid'`。

<!-- - If it's `'paid'`, you want the color to be green. If it's `'pending'`, you want the color to be gray. -->
如果是 `'paid'`，你希望颜色为绿色。如果是 `'pending'`，你希望颜色为灰色。

<!-- You can use `clsx` to conditionally apply the classes, like this: -->
你可以使用 `clsx` 有条件地应用类，如下所示：

```tsx
import clsx from 'clsx';
 
export default function InvoiceStatus({ status }: { status: string }) {
  return (
    <span
      className={clsx(
        'inline-flex items-center rounded-full px-2 py-1 text-sm',
        {
          'bg-gray-100 text-gray-500': status === 'pending',
          'bg-green-500 text-white': status === 'paid',
        },
      )}
    >
    // ...
)}
```

<!-- ### It’s time to take a quiz! -->

### 是时候做个小测验了！

<!-- Test your knowledge and see what you’ve just learned. -->
测试你的知识，看看你刚刚学到了什么。

<!-- Search for "clsx" in your code editor, what components use it to conditionally apply class names? -->
在你的代码编辑器中搜索 "clsx"，哪些组件使用它有条件地应用类名？

<!-- ## Other styling solutions -->

## 其他样式解决方案

<!-- In addition to the approaches we've discussed, you can also style your Next.js application with: -->
除了我们讨论的方法外，你还可以使用以下方法为你的 Next.js 应用设置样式：

<!-- - Sass which allows you to import `.css` and `.scss` files. -->
- Sass，它允许你导入 `.css` 和 `.scss` 文件。

<!-- - CSS-in-JS libraries such as [styled-jsx](https://github.com/vercel/styled-jsx), [styled-components](https://github.com/vercel/next.js/tree/canary/examples/with-styled-components), and [emotion](https://github.com/vercel/next.js/tree/canary/examples/with-emotion). -->
- CSS-in-JS 库，如 [styled-jsx](https://github.com/vercel/styled-jsx)、[styled-components](https://github.com/vercel/next.js/tree/canary/examples/with-styled-components) 和 [emotion](https://github.com/vercel/next.js/tree/canary/examples/with-emotion)。

<!-- Take a look at the [CSS documentation](https://nextjs.org/docs/app/building-your-application/styling) for more information. -->
查看 [CSS 文档](https://nextjs.org/docs/app/building-your-application/styling) 以获取更多信息。