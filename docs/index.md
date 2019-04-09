# docsite

这里是一个教你写**文档网站（Docsite）**的文档。

起源于为Heytea科技团队提升文档质量，而建立的一种文档方法。

同时我们把这种方法，就叫做**docsite**。

> 连自己的文档都不当成产品对待，做什么产品？

我们将文档视作为一种产品，并把产品研发文档变成一个mkdocs工具生成的网站。

##大概方法简述##

* 使用Markdown作为基本的文档书写语法；
* 对于附件——
    - 使用PlantUML语法生成流程图、用例图等各种图形；
    - Axure等工具要静态化成HTML网页；
    - Sketch、Keynotes等工具导出成图片；
- 使用SourceTree作为Git版本工具；
- 开始撰写.md格式的markdown文档；
- 使用mkdocs工具，导出文档网站；
- 使用CI工具，自动化成Nginx容器镜像，并持续文档部署；
- 配合IDaaS工具，对Nginx做用户鉴权登录；

## Doclog

2019-04-08: 初稿


## Copyright

* [mr-kelly](https://github.com/mr-kelly)<23110388@qq.com>
