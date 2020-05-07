# restful-level3(hateoas)在vue中实现

## 核心思路

- links保存在 状态管理器中 
- 如果没有父级，或者进入深层子集，就按照路径所特有参数，逐层重新获取，
- 路由结构与后端接口规则保持一致：
  - /resource/:id/resource1/:id1/resource2/:id2 
  - /resource/:id/resource1/:id1/resource2

## 几种links情况以及对应解决思路

- collection
  集合类的
- self
- update
- remove
- child


> 我的猜想：深层目录刷新本质上是数据获取的get请求，资源类型和id确定的情况完全可以使用当前path拼接成url来请求。其他类型的操作都是建立在get请求之后进行.

例如：
```
/views/:viewId/zones
```
直接采用
```
axios.get("/apis/"+this.$route.path)
```
之后的操作，就可以通过get请求返回的links里面的东西来处理

请求不同的类型资源，返回的links应该是不同的
- 集合类
- 单个对象

## 当一个资源有三个子资源时候路由该怎么设计

视图(views)下面有三种资源：
- zones -> resourse
- redirect
- dns64s

在路由配置中，是三个不同的视图入口，但是假设试图资源名为 views，那么三个的入口path 都是 "/views" 这种情况该怎么处理呢?

> 初步考虑使用 资源组合 views_zones, 代码大致

```
const path = 
```

**再router config 中定义meta url 作为根跟资源入口，可减少， views_zones解析过程（判断还是少不了）**


**另一种方式：通过设置mete.type然后对路由命名name不同来区分不同入口**，但是这种再"/views"路径下刷新时候会始终被判定为第一个"/views"




---


**前端的改动量，数据访问层，数据存储层，路由层三个层会变动；**


zone 为 叶资源名，它需要和 vue route 以及 links.children中的key保持一致, 以便于通过路由对应的资源名map到对应的子资源




- [ ] 设计 vuex 一个资源模块，对应一个module

- [ ] vuex 控制父子资源请求顺序（封装基础方法）

- [ ] 去掉services，根资源集成到vuex入口


---
我现在要实现的核心点是:

- [ ] 即使没有api文档也能通过links知道下一步操作的links
- [ ] 在深层的资源中也可以根据vue路由 访问对应数据
- [ ] 