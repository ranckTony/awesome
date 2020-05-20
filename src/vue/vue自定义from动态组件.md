# vue自定义from动态组件

vue + iview

为了减少代码冗余，我将iview的formitem单独封装，通过配置列表传入生成表单，但是业务上有一个formitem中出现两个form元素的情况

处理流程：

- CommonForm 增加一种自定义组件类型，通过type === 'component'判断
```
<component :is="item.component" v-modal="formModal[item.modal]" v-if="item.type === 'component'">
```

- 配置结构中，配置对应的
```
import ClientClassList from "./ClientClassList";
... 

{
  type: "component",
  modal: "clientClass",
  component: ClientClassList
}
```
- 编写ClientClassList, 提供 modal指令

> model = props.value + event.input, 可以用过 model: {prop,event}重新指定