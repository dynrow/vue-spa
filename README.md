## 移动端项目前端开发环境

### 架构简介
1. webpack    [文档查看地址](http://www.css88.com/doc/webpack2/)
    使用webpack进行模块分割打包, 解决了单页应用的作用域问题,可适用ES6 ,ES7语法.
1. vue                 [文档查看地址](https://cn.vuejs.org/v2/guide/)
    基于Vue框架, 开发便捷
1. vue-router  [文档查看地址](https://router.vuejs.org/zh-cn/)
    管理路由,实现单页应用 ,配合webpack可实现按需加载js文件
1. mint-ui        [文档查看地址](http://172.16.3.74:3010/#/zh-cn2)
    element ui的移动端框架
1. mockjs        [文档查看地址](http://mockjs.com/)
    生成模拟数据 ,实现前后台分离前端接口的格式定义
1. axios.js       [文档查看地址](https://www.kancloud.cn/yunye/axios/234845)
    基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中
 

### 使用步骤
> *如果安装node-sass报错,请执行<br/>
> npm install -g nrm<br/>
> nrm use cnpm<br/>
> npm install --save-dev node-sass --registry=https://registry.npm.taobao.org --disturl=https://npm.taobao.org/dist --sass-binary-site=http://npm.taobao.org/mirrors/node-sass

``` bash
#  安装依赖包
npm install
# 启动开发环境
npm run dev
# 编译发布代码, 将代码压缩,混淆,生成html页面,js拆分等...
npm run build
```

### NodeJS版本
```json
"engines": {
    "node": ">= 6.10.1",
    "npm": ">= 3.10.0"
  }
```

### License
MIT