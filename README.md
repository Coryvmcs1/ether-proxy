# ether-proxy

Ethereum mining proxy with web-interface.

**Proxy feature list:**

* Rigs availability monitoring
* Keep track of accepts, rejects, blocks stats
* Easy detection of sick rigs
* Daemon failover list


### Building on Linux

Dependencies:

  * go >= 1.6
  * geth

Install required packages:

    go get github.com/ethereum/ethash
    go get github.com/ethereum/go-ethereum/common
    go get github.com/goji/httpauth
    go get github.com/gorilla/mux
    go get github.com/yvasiyarov/gorelic

Compile:

    go build -o ether-proxy main.go


### Configuration

Configuration is self-describing, just copy *config.example.json* to *config.json* and specify endpoint URL and upstream URLs.

#### Example upstream section

```javascript
"upstream": [
  {
    "pool": true,
    "name": "EuroHash.net",
    "url": "http://eth-eu.eurohash.net:8888/miner/0xb85150eb365e7df0941f0cf08235f987ba91506a/proxy",
    "timeout": "10s"
  },
  {
    "name": "backup-geth",
    "url": "http://127.0.0.1:8545",
    "timeout": "10s"
  }
],
```


#### Running

    ./ether-proxy config.json

#### Mining

    ethminer -F http://x.x.x.x:8546/miner/5/gpu-rig -G
    ethminer -F http://x.x.x.x:8546/miner/0.1/cpu-rig -C

### Pools that work with this proxy

**Currently it's solo-only solution.**

* Report block numbers
* Report luck per rig
* Maybe add more stats
* Maybe add charts

The MIT License (MIT).
