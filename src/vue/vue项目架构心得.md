# vue项目架构心得

- 降低开发成本
- 确保项目质量
- 优化团队协作





易扩展，好维护，有规范

### 组件化 components

- 那些地方应该被抽成组件
- 如何封装一个标准的组件
- 视情况决定是否全局注册
- [更有甚至]写一个工具自动使components组件注册到全局中


##### 布局组件

- 菜单和路由结合
- 面包屑结合




### 页面 pages

每个页面的根标签需要一个专属class，[system]-[module]-[function]-[point]


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
  - 提供多个子方法 get post put del download action axios
  - 请求中止

### 全局状态 store

- 全局stata
- modules
  - moduleA
  - moduleB
  - index.js

### 资源库 assets

- css（stylus）
  - var.styl (全局变量)
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
  - css
  - svg（我更倾向，单独封装一个组件，不需要自己配置，还支持多颜色）


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
  - fetch
- 