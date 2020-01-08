# 
# Project Name

quickpod

利用 fastlane 工具链简化私有 `pod` 的发布流程

## Installation

通过 gem 安装：
```
gem install cocoapods 
```


手动安装：
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
然后控制台将输出以下信息：
```
Starting Download Fastlane Template.
Cloning into '/tmp/releasepod_fastlane_templete'...
remote: Enumerating objects: 19, done.
remote: Counting objects: 100% (19/19), done.
remote: Compressing objects: 100% (14/14), done.
remote: Total 19 (delta 3), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (19/19), done.
Download Fastlane Template Successed!
Please choose the target repo specs?
```
选择私有 Pod Spec 仓库名，然后输入当前选择的 spec 仓库地址:

 ```
 Please input the specs git repo address below:
 ```

当看到下面这段信息时，说明已经初始化成功。

```
Init fastlane configuration successed!
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

⚠️ 如果在 `pod repo lint` 或者 `pod repo push` 过程中，遇到使用依赖的包包含二进制包而引发的错误，需要修改 `fastlane/fastfile` 文件：

1. 修复 `the 'Pods-App' target has transitive dependencies that include statically linked binaries` 错误，添加 `use_libraries` 选项:
```
pod_lib_lint(allow_warnings: true, sources: target_sources, use_libraries: true)
```
2. 修复 `ld: symbol(s) not found for architecture i386`， 参考 [github issue](https://github.com/CocoaPods/CocoaPods/issues/5854#issuecomment-554912072) 添加 `skip_import_validation` 选项
```
pod_lib_lint(allow_warnings: true, sources: target_sources, use_libraries: true,skip_import_validation:true)
```

3. 遇到错误，排查问题，可以添加 `verbose` 选项。

查看帮助

```
quickpod --help 
```

## History
### 0.0.2
  * 简化初始化工作
### 0.0.1
  * 初始化 fastlane 环境
  * 更新 pod 至指定版本

  
## Ref
1. [fastlane](https://fastlane.tools)
2. [ruby doc](http://ruby-doc.org)
3. [commander](https://github.com/commander-rb/commander)
4. [一行命令发布 Pod 框架](https://juejin.im/entry/58df270f61ff4b006b1227c9)

  

