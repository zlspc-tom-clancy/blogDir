# go语言编译geth源码

## 1. 第一种方法，用 go 编译器直接编译

### 1.1 设置环境变量GOPATH

```shell
vim /etc/profile
export GOPATH=$HOME/gocode   #默认安装包的路径
export PATH=$PATH:$GOPATH/bin
source /etc/profile
```

### 1.2 使用go语言编译工具编译

首先在 `GOPATH/src` 下创建 `github.com/ethereum` 目录：

```shell
 mkdir -p $GOPATH/src/github.com/ethereum
```

然后进入上面创建的目录，下载go-ethereum项目源码：

```shell
cd $GOPATH/src/github.com/ethereum
$ git clone https://github.com/ethereum/go-ethereum.git
$ cd go-ethereum
```

下载完成后，通过以下命令编译：

```shell
go install -v ./cmd/geth
```

`go install` 命令会编译指定的源码，并在 `GOPATH/bin` 目录下生成 `geth` 可执行文件。

编译完成后，输入 `geth help` 命令，会显示 `geth` 所有的命令和选项：

```shell
cd $GOPATH/bin
./geth help
```

**参考**：

- [linux设置环境变量GOPATH](https://blog.csdn.net/qq_15437667/article/details/80482035)

- [Govendor使用](https://www.jianshu.com/p/88669ba57d04)

- [go依赖包管理工具对比](https://ieevee.com/tech/2017/07/10/go-import.html)

- [go-ethereum源码编译](https://my.oschina.net/u/2349981/blog/899260)

- [https://github.com/ethereum/go-ethereum/wiki/Developers%27-Guide](https://github.com/ethereum/go-ethereum/wiki/Developers%27-Guide)

---

## 2. 第二种方法，官方用法，make all

直接在解压后的文件中执行 `make all` 或 `make geth`，它会在当前目录的 `./build/bin/` 中编译好 geth。

使用时加上全局路径或相对路径即可，当然也可以将 bin 加入环境变量中，这样就可以不用在调用时添加绝对或相对路径了。

**参考**：[Go Ethereum](https://github.com/ethereum/go-ethereum)