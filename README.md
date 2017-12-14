# Blynk OpenWRT package

Build from source:

```bash
echo "src-git blynk git://github.com/vshymanskyy/blynk-library-openwrt.git" >> ./feeds.conf
./scripts/feeds update -a
./scripts/feeds install -p blynk -a
make menuconfig
```

### C++ client
```
Network -> Blynk -> blynk
```

### Node.js client
You need [nxhack openwrt-node](https://github.com/nxhack/openwrt-node-packages) for this.
```
Languages -> Node.js -> node-blynk-library
```

### Python 2.7 client
```
Languages -> Python -> python-blynk-library
```

## Build OpenWRT image:
```bash
make -j 5
```

## Build just Blynk:
```
make package/blynk/compile V=s
make package/node-blynk-library/compile V=s
make package/python-blynk-library/compile V=s
```

For a rebuild:
```
make package/blynk/{clean,compile,install} V=s
```
