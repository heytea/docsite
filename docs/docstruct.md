# 产品文档结构

## 内容结构
- prd：产品文档 (Product Requirement Document)
    - archi：总体产品架构
    - roles：用户角色
    - ue：原型与交互
    - functions：功能清单
    - ui：高保真UI
- rd：研发文档(Research & Development)
    - devenv：开发环境
    - archi：技术架构
    - rule：代码规范
    - models：数据模型设计
    - apis：API清单
    - quality：质量管理
    - devops：开发运维
- help：帮助文档
    - guide/ 使用说明书
    - qa/ 常见问题
    - op/ 运维手册
- release-notes：发行日志
    - upgradelog：升级日志
    - changelog：版本日志，如v1.0.3 (2020-01-01)

## 目录结构

- mkdocs.yml：网站配置
- /其它目录/：一些源文件
- /docs/：markdown文档主目录
    - /images/：相关图片
    - /axure/：原型文件
    - /prd/： 产品文档
    - /rd/： 研发文档
    - /help/：帮助文档
    - /release-notes.md：发行日志