# 安装

请注意，你必须安装Go 1.8或更高版本才能编译Delve。

## macOS

### 在macOS上安装Delve
首先请确保你有合适的编译工具链。
使用`xcode-select --install`安装xcode命令行工具。

然后你可以使用`go get`命令来安装delve
```shell 
$ go get -u github.com/go-delve/delve/cmd/dlv
```

通过这个方法，你将无法使用delve的本地后端，但无论如何，你都不需要使用到它；因为macOS上的本地后端在最新的操作系统问题上有一些已知问题，目前尚未维护。

###  编译本地后端

>什么是本地后端（native backend）

只有在你有正常理由必须需要使用本地后端时，才执行此操作。

1. 执行`xcode-select --install`
2. 如果是macOs 10.14，可以通过执行`/Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg`来手动安装旧版需要包含的头文件
3. 克隆本仓库到`$GOPATH/src/github.com/go-delve/delve`路径下
4. 到delve目录下执行`make install`（当你第一次此执行时，有些版本的macOS可能需要root权限来安装证书）

makefile将自动创建和安装自签名证书。

## Linux
### 在Linux上安装Delve

请按照以下步骤在Linux上构建和安装Delve

在Linux上安装有两种方式，

第一种是标准的`go get`方法

```shell
$ go get -u github.com/go-delve/delve/cmd/dlv
```

第二种方法是手动安装，首先确保设置了$GOPATH系统变量（比如在`~/.go`），然后执行

```shell
$ git clone https://github.com/go-delve/delve.git $GOPATH/src/github.com/go-delve/delve
$ cd $GOPATH/src/github.com/go-delve/delve
$ make install	
```

此外，如果你想在任意路径下直接执行dlv，请将`$GOPATH/bin`添加到PATH系统变量中

请注意：如果你使用Go1.5，你必须设置 `GO15VENDOREXPERIMENT=1`

才能继续。

## Windows
### 在Windows上安装Delve

请使用标准的`go get`命令在Windows上构建和安装Delve。
```shell
$ go get -u github.com/go-delve/delve/cmd/dlv
```
此外，如果你想在任意路径下直接执行dlv，请将`％GOPATH％\bin`目录添加到PATH变量中。

请注意：与Linux下安装Delve类似，如果你使用Go1.5，你必须设置 `GO15VENDOREXPERIMENT=1`

才能继续。