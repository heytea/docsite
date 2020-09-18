# 进阶

如果你是非开发或运维，一般只要把本地文档的markdown文档写好，就会自动化生成部署出文档网站了。

如果你想进一步了解这个文档网站（Docsite）怎么生成的，这里继续看。

## mkdocs工具使用

### 1. 安装Python

### 2. 安装mkdocs

```shell
pip3 install mkdocs
pip3 install mkdocs-material
```

### 3. 使用mkdocs

新建文档网站(Docsite)。

```
mkdocs new xxxxdocsite
```


运行已有的文档网站（Docsite），在带有mkdocs.yml文件的目录下执行命令：
```
mkdocs serve
```

运行后，就会持续的网站运行状态，网站地址[http://localhost:8000](http://localhost:8000)。

你的任意markdown文件需改，都会立刻生成到网站上。





## mkdocs部署

上面，我们使用了命令把文档网站在自己的电脑上运行起来了。

```
mkdocs serve
```

那么，我们如何生成出一个**真正的网站**：

```
mkdocs build
```

这时候本地就会多了个**site/**目录，这个目录就是最终的HTML网站了。

### Github Pages部署
如果你的文档放在Github上，并且是在master分支，很简单，直接命令

```
mkdocs gh-deploy
```

网站就被部署到Github Pages上了，可以使用https://xxxuser.github.io/xxxproject 查看。


### Gitlab CI部署

使用Gitlab CI，写.gitlab-ci.yml文件。

TODO Docker打包

