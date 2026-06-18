# Lucky for pfSense

这是适用于 pfSense 的 [Lucky](https://github.com/gdy666/lucky) 软件包。

安装后会在 pfSense WebGUI 的 **Services > Lucky** 菜单中添加管理页面，并提供 rc.d 服务管理、日志文件和 FreeBSD amd64 版 Lucky 主程序。

## 功能

- pfSense WebGUI 菜单入口：**Services > Lucky**
- Lucky 服务启动、停止、重启控制
- 默认 Web 管理端口：`16601`
- 默认配置目录：`/usr/local/etc/lucky`
- 默认日志文件：`/var/log/lucky.log`
- 内置官方 FreeBSD amd64 Lucky 二进制文件

## 编译

请在 FreeBSD 或 pfSense 环境中编译：

```sh
cd "pfSense/lucky for pfSense"
ABI=native ./build.sh
```

默认会优先使用源码目录中的本地文件：

```text
src/usr/local/bin/lucky_2.27.2_freebsd_x86_64.tar.gz
```

如果本地文件不存在，构建脚本会从 Lucky 上游 GitHub Release 下载对应版本。可以通过以下变量覆盖默认值：

```sh
LUCKY_VERSION=2.27.2 ./build.sh
LUCKY_ASSET=lucky_2.27.2_freebsd_x86_64.tar.gz ./build.sh
LUCKY_DOWNLOAD_URL=https://example.com/lucky.tar.gz ./build.sh
```

编译完成后的软件包位于：

```text
dist/pfSense-pkg-lucky.pkg
```

## 安装

```sh
pkg add -f dist/pfSense-pkg-lucky.pkg
```

安装完成后刷新 pfSense WebGUI，打开：

```text
Services > Lucky
```

Lucky 默认访问地址为：

```text
http://<pfSense-IP>:16601/
```

## 卸载

```sh
pkg delete -y pfSense-pkg-lucky
```

卸载时会停止 Lucky 服务，并清理软件包注册信息。
