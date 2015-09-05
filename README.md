# schalter-openwrt

* Install build dependencies according to:
  - http://wiki.openwrt.org/doc/howto/buildroot.exigence
* clone openwrt:

```bash
$ git clone git://git.openwrt.org/15.05/openwrt.git
```

* Add schalter package feed

```bash
$ cd openwrt
$ echo "src-git schalter https://github.com/c3d2/schalter-openwrt.git" >> feeds.conf.default
$ ./scripts/feeds update -a
$ ./scripts/feeds install -a
```

* Add schalter configuration

```bash
$ cat feeds/schalter/config >> .config
$ ln -s feeds/schalter/files files
$ make defconfig
```

* Optional (Add your ssh key)

```
$ cat ~/.ssh/id_rsa.pub >> files/etc/dropbear/authorized_keys
```

* Build Image

```bash
$ make -j8
$ ls -la bin/brcm2708-glibc/
```
