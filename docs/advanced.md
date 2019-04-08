# 进阶

如果你是非开发或运维，一般只要把本地文档的markdown文档写好，就会自动化生成部署出文档网站了。

如果你想进一步了解这个文档网站（Docsite）怎么生成的，这里继续看。

## 进阶：mkdocs工具

### 1. 安装Python

### 2. 安装mkdocs

```shell
pip install mkdocs
pip install mkdocs-material
``

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







