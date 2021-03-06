# 统一上线管理平台

> 上线一直是一个非常重要的操作，但目前我们的上线操作并不规范，由于流程上的不规范可能会导致比较严重的问题

## 起因
由于目前我们上线都是在本地使用Athena进行编译，然后产出可上线文件，通过人工拷贝的方式复制到上线池中进行发布，这样就会导致几个问题

* 本地编译手工拷贝要上线的文件的方式太过初级，既繁琐又可能会出错；
* 由于不同人环境的不同，安装的Athena依赖不同，可能每个人编译出来文件会不一致；
* 上线文件都是压缩文件，在 `source` 上查看代码diff太过艰难
* 回滚需要手工操作，麻烦且不够专业

## 目标

针对上述问题，我们需要一套统一上线管理平台来进行解决，它能

* 提供统一的项目上线管理，查看所有项目的上线操作记录
* 提供持续集成机制，统一的编译环境，源码提交到git后自动编译发布到真实预览环境
* 根据git改动记录，自动抽包文件提交到上线池
* 提供优秀的代码diff功能，方便查看编译后文件与线上文件的差异
* 让上线更加规范

## 项目设计

### 功能

* erp账号绑定
* 项目信息填写，对接git
* 持续集成
* 项目自动编译，抽取上线文件
* 项目发布、编译日志展示
* 代码diff
* 一键回滚机制
* 对接j-one系统

### 参考设计图
![enter image description here](http://ww4.sinaimg.cn/large/49320207jw1fa4f072benj21160l2tcr.jpg)

## 技术选型

**Vue** + **Webpack** + **KoaJs** + **ES2015**