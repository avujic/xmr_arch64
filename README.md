# XMR_ARCH64
XMR_ARCH64 is high performance Monero (XMR) CPU miner for Arch64 Linux on RPi3 board.  
Windows support inherited from xmrig/xmrig will be discarded in further development.

Originally forked from xmrig/xmrig with full development in C++11.

* [Roadmap](https://github.com/avujic/xmr_arch64/issues/8) for next releases.

<img src="http://www.eplus.systems/wp-content/uploads/2018/01/xmr_eplus_systems.png" width="619" >

#### Table of contents
* [Version](#version)
* [Features](#features)
* [Download](#download)
* [Usage](#usage)
* [Algorithm variations](#algorithm-variations)
* [Build](https://github.com/xmrig/xmrig/wiki/Build)
* [Common Issues](#common-issues)
* [Other information](#other-information)
* [Donations](#donations)
* [Contacts](#contacts)

## Version
* Code version: 0.1.1 

## Features
* High performance.
* Support for backup (failover) mining server.
* keepalived support.
* Command line options compatible with cpuminer.
* CryptoNight-Lite support for AEON.
* Smart automatic [CPU configuration](https://github.com/xmrig/xmrig/wiki/Threads).
* Nicehash support
* It's open source software.

## Download
* Binary releases: https://github.com/avujic/xmr_arch64/releases
* Git tree: https://github.com/avujic/xmr_arch64.git
  * Clone with `git clone https://github.com/avujic/xmr_arch64.git` :hammer: [Build instructions](https://github.com/avujic/xmr_arch64/wiki/Build).

## Usage
### Quick start

`./xmr_arch64`
`config.json from working folder will be used. config.json examples can be found in src folder`

### Basic example
```
./xmr_arch64 -o pool.monero.hashvault.pro:5555 -u YOUR_WALLET -p x -k
```

### Failover
```
./xmr_arch64 -o pool.monero.hashvault.pro:5555 -u YOUR_WALLET1 -p x -k -o pool.supportxmr.com:5555 -u YOUR_WALLET2 -p x -k
```
For failover you can add multiple pools, maximum count not limited.

### Options
```
  -a, --algo=ALGO       cryptonight (default) or cryptonight-lite
  -o, --url=URL         URL of mining server
  -O, --userpass=U:P    username:password pair for mining server
  -u, --user=USERNAME   username for mining server
  -p, --pass=PASSWORD   password for mining server
  -t, --threads=N       number of miner threads
  -v, --av=N            algorithm variation, 0 auto select
  -k, --keepalive       send keepalived for prevent timeout (need pool support)
  -r, --retries=N       number of times to retry before switch to backup server (default: 5)
  -R, --retry-pause=N   time to pause between retries (default: 5)
      --cpu-affinity    set process affinity to CPU core(s), mask 0x3 for cores 0 and 1
      --cpu-priority    set process priority (0 idle, 2 normal to 5 highest)
      --no-huge-pages   disable huge pages support
      --no-color        disable colored output
      --donate-level=N  donate level, default 5% (5 minutes in 100 minutes)
      --user-agent      set custom user-agent string for pool
  -B, --background      run the miner in the background
  -c, --config=FILE     load a JSON-format configuration file
  -l, --log-file=FILE   log all output to a file
      --max-cpu-usage=N maximum CPU usage for automatic threads mode (default 75)
      --safe            safe adjust threads and av settings for current CPU
      --nicehash        enable nicehash support
      --print-time=N    print hashrate report every N seconds
  -h, --help            display this help and exit
  -V, --version         output version information and exit
```

Also you can use configuration via config file, default **config.json**. You can load multiple config files and combine it with command line options.

## Algorithm variations
Since avujic/xmr_arch64 version 0.0.2  
* `--av=1` For CPUs with hardware AES.
* `--av=2` Lower power mode (double hash) of `1`.
* `--av=3` Software AES implementation. `So far, only this option works on Arch64/Rpi3` 
* `--av=4` Lower power mode (double hash) of `3`.

## Common Issues
### HUGE PAGES unavailable
* TBD


## Other information
* No HTTP support, only stratum protocol support.
* No TLS support.
* Default donation 1% (1 minute in 100 minutes) can be reduced to 0% via command line option `--donate-level`.


### CPU mining performance
* **Rpi3  ARCH64**      - 15.4 H/s (16 threads)
* **Rpi3  ARCH64**      - 07.4 H/s (08 threads)
* **Rpi3  Raspbian**    - 05.3 H/s (04 threads)

Please note performance is highly dependent on system load. The numbers above are obtained on an idle system. Tasks heavily using a processor cache, such as video playback, can greatly degrade hashrate. Optimal number of threads depends on the size of the L3 cache of a processor, 1 thread requires 2 MB of cache.

### Maximum performance checklist
* Idle operating system.
* Do not exceed optimal thread count.
* Try setup optimal cpu affinity.
* Enable fast memory (Large/Huge pages).

## Donations
* XMR: `44bF1RTZVcVc45wNiDQVTp7hwyZ5juMf8W78j1YrfChkP2og2Y44ph3WbwaVe4vUMveKAzAiA4j8xgUi29TpKXpm42GAEjd`
* LTC: `LYRerm8eDwJ8vL6ctNPceGuv8dcUcMYQ6N`

## Contacts
* `xmr@eplus.systems`


-----------------end of document-------------------------------------------
