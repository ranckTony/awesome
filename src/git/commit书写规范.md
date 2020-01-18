
commit 提交模板大致遵循

```
<type>(<scope>): <subject> [<ISSUE_ID>]

<body>

<footer>
```

### header

- type的类型包括


|前缀|描述|
|-|-|
|feat|新功能|
|fix|修复|
|doc|文档|
|style|代码格式|
|refactor|重构|
|test|测试相关|
|chore|构建或辅助工具变动|
|misc|未分类|


- scope 代码变动的影响范围

- subject 代码变动目的的简要描述

- ISSUE_ID 


### body

变动的详细说明

### footer

需求相关的文档编号


### 示例

```
git commit -m 'doc:git commit stantard'
```