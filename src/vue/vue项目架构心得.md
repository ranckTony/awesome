# vue项目架构心得

- 降低开发成本
- 确保项目质量
- 优化团队协作


### 组件化 components

- 那些地方应该被抽成组件
- 如何封装一个标准的组件
- 视情况决定是否全局注册


##### 布局组件

- 菜单和路由结合
- 面包屑结合




### 页面 pages

- pageModuleOne
  - index.vue
  - Other.vue
  - modules
    - 局部组件
- pageModuleTwo
  - index.vue
  - modules
    - 局部组件



### 路由 router


### 工具集 utils

- 正则
- 常用工具函数集
- axios二次封装
  - 请求拦截，控制token
  - 提供多个子方法 get post put del
  - 

### 全局状态 store

- 全局stata
- modules
  - moduleA
  - moduleB
  - index.js

### 资源库 assets

- css（stylus）
  - 全局变量 var.styl 
  - reset.styl
  - base.styl
  - cover.styl
  - common.styl （全局加#app权重进行一些强制修改）
- js （很少用到）
- images
  - 命名
    - bg_
    - icon_
    - [module]_
- fonts


### 测试


### 常用第三方库

- 数据可视化类
  - echart
  - d3
  - three
  - BabylonJS
  - GCanvas
- 时间处理
  - moment
- 基础通用
  - lodash
- 数据请求
  - axios
- 