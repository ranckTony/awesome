### 虚拟dom

- 虚拟dom是一个树形数据结构的js对象
- 用于反应真实dom的结构和属性
- 通过差异化比较和批量化更新达到提升性能的目的



> 操作真是dom慢的原因是绘制过程


##### 虚拟dom的数据结构

```JavaScript
{
  tag: 'div',
  props: {
    className: '',
  },
  children: [
    {
      tag: 'div',
      props: {
        id: 'header'
      },
      children: [
        {
          tag: 'h1',
          props: {
            onClick: handleClick, // 这里我不确定
          },
          children: 'Hello, World!'
        },
        {
          tag: 'p',
          children: 'How are you today?'
        }
      ]
    }
  ]
}

```