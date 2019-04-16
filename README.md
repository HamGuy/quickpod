# 
# Project Name

quickpod

利用 fastlane 工具链简化私有 `pod` 的发布流程

## Installation

克隆或下载本项目到本地

```
 git clone https://github.com/HamGuy/quickpod.git
 cd quickpod
  ./install
```

## Usage
初始化，切换到目标 pod 根目录，执行初始化命令。该命令会从预定 repo 拉取 fastlane 模版到当前 pod 下，后续操作将根据此模版进行。

```
quickpod init
```


更新 pod 到指定版本

```
qucikpod update #target_vrsion #commit_message
```

参数说明：

|  参数名称 |说明  | 备注 |
| --- | --- | --- |
| target_vesion | 目标版本号 |必填  |
| commit_message | 提交消息 |可选 ，默认为 “update version to #{target_version}” |

暂不提供 `pod repo push` 命令的 --sources 参数，如有需要，直接在 `fastlane/Fastfile` 文件中修改。

查看帮助

```
quickpod --help 
```

## History

### 0.0.1
  * 初始化 fastlane 环境
  * 更新 pod 至指定版本

  
## Ref
1. [fastlane](https://fastlane.tools)
2. [ruby doc](http://ruby-doc.org)
3. [commander](https://github.com/commander-rb/commander)
4. [一行命令发布 Pod 框架](https://juejin.im/entry/58df270f61ff4b006b1227c9)

  

