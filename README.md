## 项目目录

```
|-- CPDESIGN
|-- README.md
|-- package.json
|-- tsconfig.json
|-- yarn.lock
|-- config
| |-- env.js
| |-- modules.js
| |-- paths.js
| |-- pnpTs.js
| |-- webpack.config.js
| |-- webpackDevServer.config.js
| |-- jest
| |-- cssTransform.js
| |-- fileTransform.js
|-- mock ——配置 mock 数据
| |-- demo.js
| |-- users.js
|-- public
| |-- favicon.ico
| |-- index.html
| |-- logo192.png
| |-- logo512.png
| |-- manifest.json
| |-- robots.txt
|-- scripts
| |-- build.js
| |-- start.js
| |-- test.js
|-- src
|-- app.tsx
|-- global.less
|-- index.html
|-- index.tsx
|-- react-app-env.d.ts
|-- serviceWorker.ts
|-- assets
| |-- css
| |-- images
|-- components  ————木偶组件库
| |-- basics
| |-- NavLink
| | |-- index.tsx
| |-- Router
| | |-- index.tsx
| |-- WithRouter
| |-- index.tsx
|-- config
| |-- routerConfig.ts ————路由配置文件
|-- container ————智能组件库
|-- constants ————常量定义
| |-- actionTypes
| | |-- index.ts
| | |-- modules
| | |-- form.ts
| | |-- global.ts
| | |-- order.ts
| |-- enums
| |-- global.ts
|-- core ————核心功能库
| |-- index.ts
| |-- Axios ————内置重写 Axios 库
| | |-- Axios.ts
| | |-- InterceptorManager.ts
| | |-- dispatchRequest.ts
| | |-- index.ts
| | |-- xhr.ts
| |-- Intl ————react-hooks 多语言
| |-- InjectIntlContext.tsx
| |-- IntlContext.ts
| |-- hooks.ts
| |-- index.ts
|-- helpers ————核心库助手
| |-- Axios
| |-- data.ts
| |-- error.ts
| |-- headers.ts
| |-- url.ts
| |-- util.ts
|-- languageProvider ——配置 项目多语言结构 数据
| |-- index.js
| |-- entries
| | |-- enCN.js
| | |-- enHK.js
| |-- locales
| |-- enCN.js
| |-- enHK.js
| |-- cn ————简体中文
| | |-- common
| | |-- browser.js
| |-- hk ————繁体
| |-- common
| |-- browser.js
|-- layouts ————路由
| |-- index.less
| |-- index.tsx
|-- models ————定义数据格式
| |-- index.ts
| |-- modules
| |-- form.ts
| |-- order.ts
|-- pages ————页面
| |-- 404.tsx
| |-- home
| |-- index.tsx
| |-- styles
| |-- index.less
|-- routers ————路由控制器
| |-- index.tsx
|-- services ————网络层服务
| |-- index.ts
| |-- modules
| |-- demo.ts
|-- store ————redux 数据服务层
| |-- index.ts
| |-- action
| | |-- global.ts
| | |-- home.ts
| | |-- order.ts
| |-- reducers
| |-- formFieldsReducer.ts
| |-- index.ts
| |-- order.ts
|-- types ————type 类型定义
| |-- axios.ts
| |-- index.ts
|-- utils ————基础工具库
|-- common.tsx
|-- global.ts
|-- loadable.tsx
|-- object.js
|-- data
|-- array.js
|-- data.js
|-- date.js
|-- object.js
|-- string.js
```

## TypeScript

类型系统能够强化规范编程，TypeScript 提供定义接口。在开发大型复杂的应用软件时十分重要，一个系统模块可以抽象的看做一个 TypeScript 定义的接口。让设计脱离实现，最终体现出一种 IDL（接口定义语言，Interface Define Language），让程序设计回归本质。

通过静态类型检测可以尽早检测出程序中隐藏的的逻辑错误，对于 JavaScript 动态的弱类型语言，虽然灵活性高，但是对于初学者来说，如果不熟悉 JavaScript 内部的语言机制，很容易造成隐藏的事故。但是通过 TypeScript 的静态类型检测可以规避这些问题，因为其能够约束变量产生的类型。结合 IDE 编辑器可以推导变量对应的类型以及内部的结构，提高代码的健壮性和可维护性。

## React-Hooks

- - State Hook
- - Effect Hook
- - useContext
- - useReducer
- - useCallback
- - useMemo
- - useRef

## react-keeper(缓存页面信息)

React-Keeper 是 React 生态里一款较新的开源路由库，由国内团队开发，借鉴了 React-Router 4 很多特点，不过灵活性、实用性都强于 React-Router 很多，而且兼容 React-Router 常用用法，其文档和代码可以参见https://github.com/vifird/react-keeper。

## redux-react-hook

redux-react-hook 使用了 react 提供的 Context（上下文）功能，给顶层组件 Provide 传入了 store 对象，绑定到上下文

## React-Redux

数据流流动不自然，只有用到的数据才会引发绑定，局部精确更新，但避免了粒度控制烦恼。

## workbox webpack 插件 sw-precache-webpack-plugin

Service Worker 的出现很大程度，改变了 web app 的格局，HTTP cache 和 SW cache 有着天壤之别。这样的 HTTP 缓存机制没法弥补网页跳转带来的白屏间隙，SW cache 由于优先缓存静态资源以及接口的机制，大大减少了网络状况差（甚至断网）带来的白屏现象。优先更新本地的同时，service worker 会和后端进行一次通信，这次通信会告知静态资源是否被更改，在下次刷新的时候更改内容。

动态接口方面则会采用 runtimeCaching 进行交互，这部分也会进行动态内容的缓存，sw-toolbox 的代码将会被引入你的 sw.js 中，它会利用正则表达式匹配到你请求的接口，进行接口缓存，当该接口出现内容变化时，SW 会和后端进行一次通讯保证下一次加载的数据是最新数据，这样的更新机制分为 5 个类型。

- - networkFirst
- - cacheFirst
- - fastest
- - cacheOnly
- - networkOnly
- - networkFirst 是显示完成后，SW 优先和后端通讯，看接口是否更新，下一次刷新则是采用最新数据内容。cacheFirst 则是优先考虑缓存，如果缓存没有命中，才会去请求接口拿新数据，这个选型适合那种不经常更改的内容或者有别的更新机制。fastest 则是两个同时进行，哪个快执行哪个。cacheOnly 和 networkOnly 比较不常用。

## Mork

mork 数据引入 umi mork 抽离出来的中间键

## 网络处理

独立从浏览器中创建 XMLHttpRequests,使用 Typescript 重新实现 Axios 进行独立封装

- - 从浏览器中创建 XMLHttpRequests
- - 从 node.js 创建 http 请求
- - 支持 Promise API
- - 拦截请求和响应
- - 转换请求数据和响应数据
- - 取消请求
- - 自动转换 JSON 数据
- - 客户端支持防御 XSRF

## Tslint 配合 Git （Husky）

为了保证每次提交的 git 代码是正确的，为此我们可以使用 eslint 配合 git hook， 在进行 git commit 的时候验证 Tslint 规范

如果 Tslint 验证不通过，则不能提交。

```
  "husky": {
      "hooks": {
        "pre-commit": "lint-staged"
      }
    },
    "lint-staged": {
      "*.{ts,tsx}": [
        "tslint --project tsconfig.json"
      ]
    }
```

## Setup

```
$ npm install
```

## Running

```
$ npm start
```

## Build

```
$ npm run build
```

## Code Format

```
$ npm run prettier
```

## Code lint(引入 lint-staged 静态检查)

```
$ npm run lint-staged
```

## React-Intl 多语言支持

在 TypeScript 中使用 react-intl

# License

MIT

## antdesign 主题配色

package.json(theme)
[主题配色](https://github.com/ant-design/ant-design-mobile/blob/master/components/style/themes/default.less).
