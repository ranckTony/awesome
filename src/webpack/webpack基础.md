# webpack 基础

webpack是一个前端静态打包工具

> 学习目标

  - [ ] webpack原理，源码层面
  - [ ] 配置react typescript 的项目
  - [ ] 按需加载antd lodash moment等插件
  - [ ] 了解常用的loader，plugin
  - [ ] 学会loader编写
  - [ ] 学会plugin编写

### webpack核心概念

#### 一、入口entry 

打包过程从这里开始

默认值是 ./src/index.js


#### 输出 output

设置输出的位置和输出的文件名

```
output: {
  path: '',
  fileName: '',
}
```

#### loader

处理非js json的其他文件类型，使之成为模块

```
module: {
  rules: [
    {
      test: /.txt$/,
      use: 'txt-loader',
    }
  ]
}
```

当webpack加载到 .txt 后缀的文件时候，先试用txt-loader进行转换，然后继续后续操作


#### plugin

处理执行范围外的任务

- 打包优化
- 资源管理
- 注入环境变量



#### mode

设置开发环境

设置process.env.NODE_ENV

- development
- production


#### 