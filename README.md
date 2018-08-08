# mihuan-cms

轻量、通用、易用的企业网站系统

## 项目目标

- 轻量，只有最基本功能，使用轻量化的框架构建前后端代码
- 通用，容易拓展，适用于大多数中小企业网站功能需求
- 易用，配置简单，实现一键发布部署

## 主要功能及特性

- 可考虑脱离数据库
  - 依赖`yaml`、`markdown`等文件系统
- 后台管理系统
  - 用户及角色管理
  - 多语言管理
  - 栏目及菜单管理
  - 页面管理，可自定义字段
  - 产品(分类)管理，可自定义字段
  - 新闻管理
  - 备份管理
  - 留言管理（可选）
  - 文件管理（可选）
  - 模板管理（可选）
- 多语言支持
  - 模板文件多语言
  - 内容管理多语言
- 生成静态站点
  - 一键生成并发布静态网站

## 项目进度

### 初步思考

本项目的难点在于生成静态站点，
现成的静态站点生成器很多，眼花缭乱，但是都没有CMS的概念，
简单说就是没有一个可视化的后台管理功能，
都是直接编辑代码然后利用命令生成静态页面，
这样的情况对于开发人员很简单，但是对于普通的网站管理员，友好度等于零！

根据初步的研究，形成了两个思路：

#### 思路一

- 搭建一个前端操作界面（后台管理系统）
- 搭建一个后端服务器
- 服务器部署`Jekyll`、`Hugo`或`Hexo`等静态站点生成器项目
- 后端通过管理服务器中相应`markdown`、`yaml`文件来修改`Jekyll`项目代码
- 发布则直接调用`Jekyll`的`build`命令

有点：

- 无需数据库

难点：

- 在于如何方便的操作`markdown`、`yaml`文件

缺点：

- 由于没有数据库，功能会比较受限

#### 思路二

- 搭建一个前端操作界面（后台管理系统）
- 搭建一个后端服务器+数据库（或json），与前端组成一个传统的CMS系统
- 服务器部署`Gatsby`、`React Static`或`Nuxt.js`等静态站点生成器项目
- `Gatsby`通过调用后端数据接口生成静态站点
- 发布则调用`Gatsby`的`build`命令
- 此方案也可以不用数据库，数据源可以是`json`、`markdown`等文件格式，然后后端主要工作就是操作各种`json`文件了
