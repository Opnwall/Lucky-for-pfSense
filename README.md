# Lucky for pfSense

pfSense package for [Lucky](https://github.com/gdy666/lucky), providing a WebGUI menu entry under **Services > Lucky**, rc.d service management, logs, and the official FreeBSD amd64 Lucky binary.

## Build on pfSense

```sh
cd "pfSense/lucky for pfSense"
ABI=native ./build.sh
```

The build script downloads `lucky_2.27.2_freebsd_x86_64.tar.gz` from the upstream GitHub release by default. Override `LUCKY_VERSION`, `LUCKY_ASSET`, or `LUCKY_DOWNLOAD_URL` if needed.

## Install

```sh
pkg add -f dist/pfSense-pkg-lucky.pkg
```

After installation, refresh the pfSense WebGUI and open **Services > Lucky**. The Lucky backend listens on port `16601` by default.
