## 简要说明
vue-cli-old是使用旧版vue-cli生成的项目骨架，因为旧版和新版有一个比较大的区别是：新版没有了`dev-server.js`和`dev-client.js`配置文件，可以使用它和新版做个横向对比。几乎所有的代码都带有说明及参考链接，方便理解。    
## 项目结构
```
│  .babelrc						// babel配置
│  .postcssrc.js					// CSS预编译器配置
│  index.html						// 入口页面
│  package.json					        // npm配置
├─build							// 构建脚本目录，使用 npm run * 时就是执行这里的文件
│      build.js						// 生产环境构建脚本
│      check-versions.js				// 检测Node.js和npm版本
│      dev-client.js					// 本地服务器热重载配置
│      dev-server.js					// 运行本地服务器的配置
│      utils.js						// 构建用的相关工具方法
│      vue-loader.conf.js				// css加载器配置
│      webpack.base.conf.js			        // webpack基础配置
│      webpack.dev.conf.js			        // webapck开发环境配置
│      webpack.prod.conf.js			        // webpack生产环境配置
├─config					        // 项目配置目录，主要是一些变量的配置，以供构建使用
│      dev.env.js					// 开发环境变量
│      index.js						// 基本环境变量
│      prod.env.js					// 生产环境变量
├─src							// 源代码目录
│  ├─assets						// 资源文件目录
│  ├─components					        // 组件目录
│  ├─router						// 路由目录
└─static					        // 静态资源目录
```
## 详细解释
### build/dev-server.js
使用 npm run dev 时运行该脚本，主要完成下面的操作：
- 检查Node.js和npm的版本
- 引入相关插件和配置
- 创建express服务器和webpack编译器
- 配置`webpack-dev-middleware`开发中间件和`webpack-hot-middleware`热重载中间件
- 加载代理服务和以上中间件
- 配置静态资源文件目录，交由express服务器管理
- 启动服务器，监听指定端口
- 自动使用默认浏览器打开指定uri

### build/dev-client.js
该模块订阅dev-server中发布的强制刷新事件，当html内容发生改变时，强制刷新页面

### build/build.js
使用命令 npm run build 时执行该脚本，通过编译、压缩、拷贝等操作，将源代码打包

### build/check-version.js
根据package.json中的engines属性，检查当前Node.js和npm环境

### build/utils.js
构建时用到的工具

### build/vue-loader.conf.js
vue使用的一些加载器的配置

### build/webpack.base.conf.js
webpack的基本配置

### build/webpack.dev.conf.js
webpack开发环境的配置

### build/webpack.pro.conf.js
webpack生产环境的配置

### config/index.js
导出构建时需要的一些基本变量配置

### config/dev.env.js
导出开发环境变量

### config/prod.env.js
导出生产环境变量