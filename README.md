# OpenWRT-Blynk-packages
Blynk package for OpenWRT

Build from source:

```bash
echo "src-git blynk git://github.com/vshymanskyy/blynk-library-openwrt.git" >> ./feeds.conf
./scripts/feeds update -a
./scripts/feeds install -p blynk -a
make menuconfig
```

Select: Network -> Blynk -> blynk

```bash
make -j 5
```

To build just Blynk:
```
make package/blynk/compile V=s
```

For a rebuild:
```
make package/blynk/{clean,compile,install} V=s
```
