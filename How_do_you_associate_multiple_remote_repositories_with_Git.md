
# 背景


通常情况下，一个本地Git仓库对应一个远程仓库，每次pull和push仅涉及本地仓库和该远程仓库的同步；然而，在一些情况下，一个本地仓库需要同时关联多个远程仓库，比如：同时将一个项目发布在<a href="https://www.github.com" target="_blank">Github</a>
和<a href="https://https://gitee.com/" target="_blank">Gitee</a>上，以兼顾国内外的访客。

如何将多个远程存储库与Git关联？


首先，用` git remote add <name> <url> `添加一个远程仓库，其中` name `可以任意指定（对应上面的` origin `部分）。
比如：

```
$ git remote add origin 
git@giteecom:shunshidiedai/java-web-develop.git
```

再查看本地仓库所关联的远程仓库：

```
$ git remote -v
origin	git@gitee.com:shunshidiedai/java-web-develop.git (fetch)
origin	git@gitee.com:shunshidiedai/java-web-develop.git (push)
```

已经成功关联一个远程仓库Gitee，我们给现有的远程仓库添加额外的URL。使用`git remote set-url -add <name> <url>`添加一个远程地址。
比如：

```
$ git remote set-url --add origin git@github.com:Hocy-jia/Learning-Git.git
 ```

 我们再次查看所关联的远程仓库：

 ```
 $ git remote -v
origin	git@gitee.com:shunshidiedai/java-web-develop.git (fetch)
origin	git@gitee.com:shunshidiedai/java-web-develop.git (push)
origin	git@github.com:Hocy-jia/Learning-Git.git (push)
 ```
这样设置后,我们可以正常使用push和pull，不需要进行调整。
如：
```
$ git push origin master
```
```
$ git pull origin master
```

本次内容中涉及到的Git指令略去了许多不常用的参数，如需更加详细的说明，可以查阅Git文档，或者直接在命令行运行`git remote --help`。