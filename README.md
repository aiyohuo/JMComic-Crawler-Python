# Python API For JMComic (禁漫天堂)

封装了一套可用于爬取JM的Python API.

简单来说，就是可以通过简单的几行Python代码，实现下载JM上的本子到本地，并且是处理好的图片.

**友情提示：珍爱JM，为了减轻JM的服务器压力，请不要一次性爬取太多本子，西门🙏🙏🙏**.

## 安装教程

* 通过pip官方源安装（推荐）

  ```shell
  pip install jmcomic -i https://pypi.org/project --upgrade
  ```
* 本地安装

  ```shell
  pip install -e ./
  ```

## 快速上手

使用下面的两行代码，即可实现功能：把某个本子（album）里的所有章节（photo）下载到本地

```python
import jmcomic  # 导入此模块，需要先安装.
jmcomic.download_album('422866')  # 传入要下载的album的id，即可下载整个album到本地.
# 上面的这行代码，还有一个可选参数option: JmOption，表示配置项，
# 配置项的作用是告诉程序下载时候的一些选择，
# 比如，要下载到哪个文件夹，使用怎样的路径组织规则（比如[/作者/本子id/图片] 或者 [/作者/本子名称/图片]）.
# 如果没有配置，则会使用 JmOption.default()，下载的路径是[当前工作文件夹/本子名称/图片].
# 如果你想要配置，请参考assets/config/和usgae/下的文档和示例.
```

进一步的使用可以参考usage文件夹下的示例代码: `getting_started.py` `sample_usage.py`

## 项目特点

- **绕过Cloudflare的反爬虫**
- 支持使用**Github Action**下载漫画，不会编程都能用（[教程：使用Github Actions下载禁漫本子](./assets/docs/教程：使用Github%20Actions下载禁漫本子.md)）
- 可配置性强
  - 不配置也能使用，十分方便
  - 配置可以从**配置文件**生成，支持多种文件格式，无需写Python代码
  - 配置点有：`是否使用磁盘缓存` `图片类型转换` `下载路径` `请求元信息（headers,cookies,代理）等 `
- 可扩展性强
  - 支持自定义本子/章节/图片下载前后的回调函数
  - 支持自定义debug日志的开关/格式
  - 支持自定义Option/Client/实体类
- 支持重试和域名切换机制
- 多线程下载（可细化到一图一线程，效率极高）
- 跟进了JM最新的图片分割算法（2023-02-08）

## 使用小说明

* Python >= 3.7
* 个人项目，文档和示例会有不及时之处，可以Issue提问

## 项目文件夹介绍

* assets：存放一些非代码的资源文件

  * config：存放配置文件
  * docs：项目文档
* src：存放源代码

  * jmcomic：`jmcomic`模块
* tests：测试目录，存放测试代码，使用unittest
* usage：用法目录，存放示例/使用代码

## 感谢以下项目

### 图片分割算法代码+禁漫移动端API

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=tonquer&repo=JMComic-qt)](https://github.com/tonquer/JMComic-qt)
