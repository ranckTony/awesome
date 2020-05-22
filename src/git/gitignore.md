# gitignore

gitignore里面的配置可以指定不提交的文件，或者文件夹

但是如果指定的文件已经属于版本管理的文件，该指定就不会生效

处理办法可以先备份删除提交后，再指定配置



或者 

```
git rm -r  --cached  config/index.js
git add .
git commit -m "更新提交"
```