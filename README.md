## tvbox_tools
写这个工具的主要原因是网上各种接口虽然很多，但是重复率也高，失效率也高，所以想做个整理工具，接口看起来整洁。

## 功能概述
- 支持多仓、单仓、线路接口的私有化(json和对应的jar文件下载到本地，经过格式化后推送到自己的git仓库)
- 移除失效线路
- 移除名称中的emoj表情
- 根据hash去重线路

### 更新说明
- V1.8版本 移除agit.ai支持；all.json线路排序；
- V1.7版本 优化git clone速度，仓库重置提交记录
- V1.6版本 不规范json兼容优化，http请求timeout默认3s，优化移除emoji表情
- V1.5版本 bug修复，github.com支持优化
- V1.4版本 bug修复，jar下载失败，不会创建0字节jar文件，保留原jar链接
- V1.3版本 支持github.com
- V1.2版本 支持jar本地化
- V1.1版本 bug修复，仅支持agit.ai，不支持jar本地化
- V1.0版本 支持单线路、单仓、多仓下载，输出：{target}(默认tvbox.json)，和url填写的源内容一致；all.json是仓库中所有下载的历史线路总和，并且去重了内容相同的线路

## 使用方法：

#### demo
```
https://mirror.ghproxy.com/https://raw.githubusercontent.com/fish2018/tvbox/master/tvbox.json
https://mirror.ghproxy.com/https://raw.githubusercontent.com/fish2018/tvbox/master/all.json
```

#### 参数选项 
docker run时使用-e选项通过环境变量传参

- [ * ] username or u 指定用户名
- [ * ] token github.com中设置的token
- [ * ] url 指定要下载的源，不指定url默认会下载tvbox助手上的线路
- repo 指定你的代码仓库名，默认tvbox
- target 指定你想保存的json文件名，默认tvbox.json
- num 多仓时可以指定下载前num个仓库源
- timeout http请求超时，默认3s

#### 示例:
首先在github.com上创建自己的代码仓库，推荐命名'tvbox'

```bash
docker run --rm  -e username=XXX -e token=XXX -e url='xxx' 2011820123/tvbox
```

国内可以使用代理拉取镜像
```bash
docker run --rm  -e username=XXX -e token=XXX -e url='xxx' dockerproxy.com/2011820123/tvbox:latest
```
  
