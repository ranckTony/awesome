# vue前端开发规范

  - [目的](#goal)
  - [项目结构](#structure)
  - [组件编写](#component)
    - [模板编写](#template)
    - [脚本编写](#script)
    - [样式编写](#style)
  - [ES规范](#es)
  - [less](#less)


<h3 id="goal">目的</h3>

编写前端开发规范是为了保证项目代码风格的一致性，写出性能更优，可读性更好，逻辑更合理的代码，从而提升项目的代码质量和可维护性。

编写文档初期难免会因为个人技术视野和当时遇到的客观项目需求导致规范在后面的使用过程中发现不合理的地方，希望规范使用者不要迷信于权威，勇于提出优化方案使得规范更加规范。


<h3 id="structure">项目结构</h3>

```

|-src
| |-assets
| |-components
| |-router
| |-services
| | |-index.js
| | |-dnsApi.js
| | |-dhcpApi.js
| |-store
| | |-index.js
| | |-modules
| | | |-dns.js
| |-util
| | |-reg.js
| | |-tool.js
| | |-index.js
| |-views
| | |-dns
| |  |-moduleA
| |  |-moduleB
| | |-dhcp
| | |-ipam
| |-App.vue
| |-main.js
 
```

- 方法命名
	- 操作方法
	- 数据处理方法
- 文件命名: 组件文件采用大驼峰命名相关组件使用相同前缀，基础组件用Base前缀



<h3 id="component">组件编写</h3>

- 文件结构
```
|-components
 |-BaseButton
 |-BaseInput
 |-Search
 |-SearchButton
```
<h5 id="template">模板编写</h5>

<h5 id="script">脚本编写</h5>
- vue属性方法次序

```
- components
- props
- data
- computed
- created
- mounted
- methods
- filter
- watch
```

- 方法
  
vue 组件中的方法通常用于请求数据，数据转换，事件回调，因此命名方面建议加上特定的前缀,小驼峰

```javascript
methods: {
    getDataList () {},
    executeDataList () {},
    handleSubmit () {},
}
```
    



- 指令书写：
  - v-for 必须使用key，并且不能直接使用索引或者其他不具备唯一标识的数据充当key；
  - v-if和v-for不能在同一个标签上使用，v-if应该放在外层

- style
  - 指定less作为
  - 组件内部专属样式设置scoped
  - 选择器层级不超过3层



<h3 id="es">ES规范</h3>
  
- 代码缩进：2个空格
- 字符串使用单引号
- 小驼峰命名
```javascript
let dateList = []

function handleOpenCreate() {}
```
- const let 代替 var

```javascript
const MAX_NUMBER = 10;
let foo;
```
- 对象，数组解构

```javascript
const [count, setCount] = useState(0);
const {id, query} = params;
const [head, , , end] = [1, 2, 3, 4];
const [head, ...tails] = [1, 2, 3, 4]; // tails [2, 3, 4]

```

- 对象属性简写，简写前置

```javascript
function createParams (id) {
    const query = '项目';
    return {
        id,
        query,
        createTime: '2020-02-02',
    };
}
```

- 展开运算法，浅拷贝

```javascript
const arr = [1, 2, 4];
const rest = [...arr];
```
- 转换成数组 ...
- 合理省略函数的花括号
```javascript
function add (...agr) {
    return agr.reduce((result, current) => result + current, 0)
}
```
- 直接迭代 Array.form() 避免创建新数组


  - 
- 使用模版字符串处理拼接
  
```javascript
const name = 'world';
const str = `hello ${name}`
```
  
- 单行注释

```javascript
// 选中标记
let flag;
```



- 多行注释

```javascript
/**
 * @brief:简单描述:l两个数字相加
 * @param {number} a
 * @param {number} b
 * @return {number}
 **/
function add(a, b){
	return a + b;
}
```

<h3 id="less">LESS规范</h3>

- 局部代码设置代码块类，合理父子选择器关系
- 尽量减少选择器层级,不能超过3级
- css属性简写，margin padding border 小数等
- 选择器名使用小写，多个单词'-'连接
- 减少样式覆盖，使用更精确的选择器
- 能用英文少用数字
- 动画实现方式transition优先于animation
- 颜色方面使用16进制，透明度rgba
- 样式声明顺序





