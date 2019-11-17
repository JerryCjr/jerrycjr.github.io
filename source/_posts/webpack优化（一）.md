---
title: webpack优化（一）
date: 2019-11-17 19:29:01
tags:
  - Webpack
categories: Web
---
优化之前

![未优化之前](/images/webpack/1.png)

优化之后

![未优化之前](/images/webpack/2.png)

## update plugin + loader

### 项目中的依赖项

```json
"devDependencies": {
  "extract-text-webpack-plugin": "^3.0.0",
  "friendly-errors-webpack-plugin": "^1.6.1",
  "html-webpack-plugin": "^2.30.1",
  "optimize-css-assets-webpack-plugin": "^3.2.0",
  "uglifyjs-webpack-plugin": "^1.1.1",
  "webpack": "^3.6.0",
  "webpack-bundle-analyzer": "^2.9.0",
  "webpack-dev-server": "^2.9.1",
  "webpack-merge": "^4.1.0"
}
```

### 安装最新稳定版本

#### plugin
```bash
npm i webpack@latest webpack-merge@latest webpack-dev-server@latest webpack-bundle-analyzer@latest uglifyjs-webpack-plugin@latest optimize-css-assets-webpack-plugin@latest html-webpack-plugin@latest friendly-errors-webpack-plugin@latest extract-text-webpack-plugin@latest -D
```

注意还包括webpack-cli

```bash
npm i webpack-cli@latest -D
```

#### loader

```
npm i vue-loader@latest eslint-loader@latest -D
```

## mode

升级之后mode属性是必须制定的 否则按照约定优于配置原则 将默认按照production编译

### webpack.dev.conf.js

```javascript
const devWebpackConfig = merge(baseWebpackConfig, {
  mode: 'development',
  ...
})
```

### webapck.prod.conf.js

```javascript
const webpackConfig = merge(baseWebpackConfig, {
  mode: 'production',
  ...
})
```

## 删除不需要的插件或者配置

### CommonsChunkPlugin

[CommonsChunkPlugin was removed -> optimization.splitChunks, optimization.runtimeChunk](https://github.com/webpack/webpack/releases/tag/v4.0.0)

```javascript
optimization: {
  splitChunks: {
    cacheGroups: {
      vendor: {
        test: /[\\/]node_modules[\\/]/,
        name: 'vendor',
        chunks: 'all',
        priority: 2,
        minChunks: 2
      },
      common: {
        test: /.js$/,
        name: 'common',
        chunks: 'initial',
        priority: 1,
        minChunks: 2
      }
    }
  },
  runtimeChunk: { name: 'runtime' }
}
```

### uglifyjs-webpack-plugin

生产环境下会走默认配置 如果需要定制一些配置的话再添加 在这里我直接删除了原先的配置并且移除了这个插件

```
npm uninstall uglifyjs-webpack-plugin
```

### extract-text-webpack-plugin

[推荐的替代方案：mini-css-extract-plugin](https://juejin.im/post/5c3d81f451882524f2302bbd)

### Vue loader

[vue-loader配置](https://juejin.im/post/5c3d81f451882524f2302bbd)


---

## 引用

* https://github.com/webpack/webpack/releases/tag/v4.0.0
* https://juejin.im/post/5c3d81f451882524f2302bbd
* http://louiszhai.github.io/2019/01/04/webpack4/
* https://blog.csdn.net/u013243347/article/details/88547730 
* https://www.twblogs.net/a/5c45dd21bd9eee35b21eef06/zh-cn
