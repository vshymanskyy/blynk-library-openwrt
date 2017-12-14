# Blynk OpenWRT package

Build from source:

```bash
echo "src-git blynk git://github.com/vshymanskyy/blynk-library-openwrt.git" >> ./feeds.conf
./scripts/feeds update -a
./scripts/feeds install -p blynk -a
make menuconfig
```

### Node.js client
You need [nxhack openwrt-node](https://github.com/nxhack/openwrt-node-packages) for this.
```
Languages -> Node.js -> node-blynk-library
```
Node.js Example:
```js
const Blynk = require('blynk-library');

// Initialize Blynk
let AUTH = 'YourAuthToken';
let blynk = new Blynk.Blynk(AUTH);
let v1 = new blynk.VirtualPin(1);

// Register virtual pin handler
v1.on('write', function(param) {
    console.log('Got a value:', param);
});
```

### Python 2.7 client
```
Languages -> Python -> python-blynk-library
```
Python Example:
```python
import BlynkLib

# Initialize Blynk
AUTH = 'YourAuthToken'
blynk = BlynkLib.Blynk(AUTH)

# Register virtual pin handler
@blynk.VIRTUAL_WRITE(1)
def v1_write_handler(value):
    print('Got a value: {}'.format(value))

# Start Blynk (this call should never return)
blynk.run()
```

### C++ client
```
Network -> Blynk -> blynk
```
C++ Example:
```cpp
#include <BlynkApiLinux.h>
static BlynkTransportSocket blynkTransport;
BlynkSocket Blynk(blynkTransport);

const char* AUTH = "YourAuthToken";

BLYNK_WRITE(V1) {
    printf("Got a value: %s\n", param[0].asStr());
}

int main(int argc, char* argv[]) {
    Blynk.begin(auth);

    while (true) {
        Blynk.run();
    }

    return 0;
}
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
