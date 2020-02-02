# Stage1st论坛专楼下载器

## 简介

使用python实现，原理是用requests下载帖子每页的html，然后将其中所有css、script和图片保存至本地

- 优势
   * 下载后的帖子可以离线翻页，方便阅读
   * 不同帖子共用css、图片等资源，节约空间
   * 自动将新浪外链图片的https替换为http
   * 包含登录功能，可下载需要权限的帖子
   
- 不足
   * 删除下载的帖子时无法删除其中图片
   * ~~下载速度较慢~~已通过多线程下载提速
   * GUI非常丑
   
---
## V0.2更新
   * 添加了异常处理
   * 修复了chrome无法正常加载css的问题
   * 下载部分加入了多线程进行提速
---

程序非常简单，下载部分源码在[S1_downloader.py](https://github.com/shuangluoxss/Stage1st-downloader/blob/master/S1_downloader.py)中，熟悉python的坛友可以在此基础上自行修改

为方便使用，用PyQt5做了一个简陋的GUI并打包了成exe，GUI相关源码在[S1-downloader_GUI.py](https://github.com/shuangluoxss/Stage1st_downloader/blob/master/S1-downloader_gui.py)中

## 使用方法
**（网页保存位置默认为程序运行位置）**
- python版本
   * 下载地址：[S1_downloader.py](https://github.com/shuangluoxss/Stage1st-downloader/blob/master/S1_downloader.py)
   * `WorkThread.download_thread(url)`下载url所在专楼的所有页，其余参数用法见注释
   * ~~会python的直接看源码去，懒得写说明了~~
- exe版本
   * 下载地址：[S1_downloader_v0.2.zip](https://github.com/shuangluoxss/Stage1st-downloader/releases/download/v0.2/S1_downloader_V0.2.zip)
   * 双击运行，在帖子地址中粘贴帖子地址，点开始下载即可
   * 若需要登录，点击“登录”，输入账号密码
- 命令行版本
   - 使用方法：
      - python3 ./S1_downloader_cli.py [-h] [-u USER] [-p PASSWORD] [-v] threads [threads ...]
      - -h, --help 显示帮助
      - -u USER, --user USER S1 账号名
      - -p PASSWORD, --password PASSWORD 账号密码
      - -v, --verbose 显示调试信息（当出错时使用）

注意：不要将程序放在C盘**系统文件夹**内，以免因权限问题报错

## 使用建议
- 由于下载速度主要由论坛响应速度决定，建议在论坛流量较小时使用
- 由于论坛帖子有大量共用素材（麻将脸等），当这部分素材下载完毕后，帖子下载速度会得到显著提升
- 由于作者水平所限，程序大概会有很多bug，如果大家使用中遇到问题欢迎在论坛或这里反馈，有希望添加的功能也欢迎提出~
