# 定制Ghost博客

## 升级Ghost

Ghost升级比较简单，主要是下载官网最新发布的安装包替换旧的就行了。

1. 下载最新的Ghost源码包，https://ghost.org/zip/ghost-latest.zip
2. 把原来ghost目录内的`content`目录和`config.js`保留，其它的替换掉
3. 

## Ghost开发

### 问题

1. 开发模式下，如果是在虚拟机上运行的，要把`config.js`上的`server`地址由`127.0.0.1`改为`0.0.0.0`。
