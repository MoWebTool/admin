[![dependencies](https://david-dm.org/ndfront/admin.svg?style=flat-square)](https://david-dm.org/ndfront/admin)
[![devDependency Status](https://david-dm.org/ndfront/admin/dev-status.svg?style=flat-square)](https://david-dm.org/ndfront/admin#info=devDependencies)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [admin](#admin)
  - [1 目录说明](#1-%E7%9B%AE%E5%BD%95%E8%AF%B4%E6%98%8E)
  - [2 关键词](#2-%E5%85%B3%E9%94%AE%E8%AF%8D)
  - [3 使用到的前端技术](#3-%E4%BD%BF%E7%94%A8%E5%88%B0%E7%9A%84%E5%89%8D%E7%AB%AF%E6%8A%80%E6%9C%AF)
  - [4 环境搭建](#4-%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA)
    - [4.1 必需](#41-%E5%BF%85%E9%9C%80)
    - [4.2 可选](#42-%E5%8F%AF%E9%80%89)
  - [5 安装依赖](#5-%E5%AE%89%E8%A3%85%E4%BE%9D%E8%B5%96)
  - [6 开发调试](#6-%E5%BC%80%E5%8F%91%E8%B0%83%E8%AF%95)
    - [6.1 方案一](#61-%E6%96%B9%E6%A1%88%E4%B8%80)
    - [6.2 方案二（推荐）](#62-%E6%96%B9%E6%A1%88%E4%BA%8C%EF%BC%88%E6%8E%A8%E8%8D%90%EF%BC%89)
  - [7 代码静态检查](#7-%E4%BB%A3%E7%A0%81%E9%9D%99%E6%80%81%E6%A3%80%E6%9F%A5)
    - [7.1 手动检查](#71-%E6%89%8B%E5%8A%A8%E6%A3%80%E6%9F%A5)
    - [7.2 自动检查](#72-%E8%87%AA%E5%8A%A8%E6%A3%80%E6%9F%A5)
  - [8 打包构建](#8-%E6%89%93%E5%8C%85%E6%9E%84%E5%BB%BA)
  - [9 自动化测试](#9-%E8%87%AA%E5%8A%A8%E5%8C%96%E6%B5%8B%E8%AF%95)
  - [10 国际化支持](#10-%E5%9B%BD%E9%99%85%E5%8C%96%E6%94%AF%E6%8C%81)
    - [10.1 输出](#101-%E8%BE%93%E5%87%BA)
    - [10.2 提取规则](#102-%E6%8F%90%E5%8F%96%E8%A7%84%E5%88%99)
  - [11 使用帮助](#11-%E4%BD%BF%E7%94%A8%E5%B8%AE%E5%8A%A9)
  - [12 工具推荐](#12-%E5%B7%A5%E5%85%B7%E6%8E%A8%E8%8D%90)
    - [12.1 代码格式化](#121-%E4%BB%A3%E7%A0%81%E6%A0%BC%E5%BC%8F%E5%8C%96)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# admin

> Social 管理系统，支持国际化，实现基于角色的权限控制

## 1 目录说明

不要用中文做目录名

```
js
├─.bin ------ 存放命令脚本的文件夹
├─.i18n ----- 国际化资源
├─config ---- 基础配置
├─coverage -- 测试覆盖率输出
├─mocks ----- 本地开发模拟数据
├─server ---- 本地开发服务配置
├─src ------- 源文件目录
├─tests ----- 测试脚本
└─webpack --- Webpack 基础配置
```

```
src
├─apis ------ 接口配置
├─app ------- 业务文件
├─misc ------ 其它通用的模块
├─model ----- RESTful 的数据模型
├─origins --- 各服务地址配置
├─routes ---- 路由配置
├─static ---- 静态文件
├─template -- 存放首页模板
└─theme ----- 主题样式
```

## 2 关键词

- 模块化：commonjs、ES6
- 组件化：npm、[ndfront](https://github.com/ndfront)
- 模板化：handlebars
- 热重载：[HMR](http://webpack.github.io/docs/hot-module-replacement.html)

## 3 使用到的前端技术

- [node](https://nodejs.org/)
- [npm](https://npmjs.com/)
- [webpack](http://webpack.github.io/)
- [postcss](http://postcss.org/)
- [karma](https://karma-runner.github.io/)
- [koa](http://koajs.com/)
- [eslint](http://eslint.org/)
- [babel](https://babeljs.io/)
- [handlebars](http://handlebarsjs.com/)

## 4 环境搭建

### 4.1 必需

- [node](https://nodejs.org/)
- [editorconfig](http://editorconfig.org/)

### 4.2 可选

- [cmder](http://cmder.net/)
- [git](https://git-scm.com/)

  安装中选择

  - Use Git and optional Unix tools from the Windows Command Prompt
  - Checkout as-is, commit as-is

  安装后执行

  ```bash
  $ git config --global core.autocrlf false   # 禁止自动转换换行符
  ```

## 5 安装依赖

**请确保 npm -v >= 3.6.0**

```bash
$ cd path/to/js
$ npm install -r https://registry.npm.taobao.org  # 使用淘宝源，加快安装速度
```

P.S. **当 `package.json` 的 `dependencies` 有更新时，需要重新执行上述脚本**

移除不再被依赖的模块

```bash
$ npm prune
```

处理重复的模块

```bash
$ npm dedupe
```

## 6 开发调试

### 6.1 方案一

启动本地服务，使用本地虚拟环境的数据

```bash
$ npm start
```

或启动本地服务，同时使用线上环境的数据

```bash
$ npm run dev:DEVELOPMENT     # 开发
$ npm run dev:DEBUG           # 测试
$ npm run dev:PRESSURE        # 压测
$ npm run dev:PREPRODUCTION   # 预生产
```

浏览器访问

```bash
$ open http://127.0.0.1:3000
```

### 6.2 方案二（推荐）

启动本地服务

```bash
$ npm start
```

然后使用 [fiddler](http://www.telerik.com/fiddler) 等，将线上代码映射到本地进行开发调试，以下是 `fiddler.fax` 的相关配置：

```xml
<ResponseRule Match="regex:http://admin\..+\.web\.nd/$" Action="http://localhost:3000/" Enabled="true" />
<ResponseRule Match="regex:http://admin\..+\.web\.nd/((?!v0\.).*)" Action="http://localhost:3000/$1" Enabled="true" />
```

浏览器访问

```bash
$ open http://admin.dev.web.nd   # 或其它线上地址
```

## 7 代码静态检查

### 7.1 手动检查

使用 eslint 检查代码规范

```bash
$ npm run lint
```

使用 eslint 检查代码规范并自动修复

```bash
$ npm run lint:fix
```

### 7.2 自动检查

编辑器安装 eslint 相关插件，实时检查代码规范

## 8 打包构建

buid 文件生成在 js 同级的 webapp 目录下

```bash
$ npm run deploy
```

P.S. 执行 `npm run deploy` 将自动执行静态检查，检查未通过则退出

## 9 自动化测试

*持续完善中*

```bash
$ npm test
# $ npm run test:dev
```

## 10 国际化支持

生成中文/英文/印尼文翻译，合并已翻译与待翻译，待翻译项以 zh-CN 中对应的值填充

```bash
$ npm run i18n:[lang]   # 可选，默认 zh-CN
```

### 10.1 输出

- `src/static/i18n/**/*.JSON`，用于更新到数据库
- `.i18n/**/*.JSON`，用于提交给翻译人员进行翻译，[提交地址](http://svn.sdp.nd/svn/social-svn-folder/doc/多语言/Admin)

### 10.2 提取规则

- 项目中使用 `__` 方法的字符串
  - 包括 `js` 与 `handlebars`
    - 包括 `src` 目录
    - 包括 `nd-***` 模块
  - 包括项目 `package.json` 中的 `description` 字段
- 字典目录中的接口错误提示信息
  - 字典目录为 `.i18n`，定期更新翻译资源

## 11 使用帮助

- `docs` 目录下会不断增加文档
- `app/demo` 目录下会不断增加样例
- 到 admin 群里发问
- 联系 980071

## 12 工具推荐

### 12.1 代码格式化

- [esformatter](https://github.com/millermedeiros/esformatter)
  - [vim-esformatter](https://github.com/millermedeiros/vim-esformatter)
  - [sublime-esformatter](https://github.com/piuccio/sublime-esformatter)
  - [atom-esformatter](https://github.com/sindresorhus/atom-esformatter)
