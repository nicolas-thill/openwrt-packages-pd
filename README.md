# openwrt-packages-pd

A collection of packages for experimenting with [Pure Data](https://puredata.info/) on [OpenWrt](https://openwrt.org/).

## Instructions

Add this packages feed to your OpenWrt build environment.

1. Add the following line to the `./feeds.conf` file.

```
src-git pd https://github.com/psycho-nico/openwrt-packages-pd.git

```
2. Update the packages feeds

```
./scripts/feeds update
```

3. Install packages from this feed

```
./scripts/feeds install -d m -p pd
```
