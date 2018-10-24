### LeshaCat fork of BootNOMP ([1301313Y/BootNOMP:master](https://github.com/1301313Y/BootNOMP))
***Current Version: v1.1.4***
#### [leshacat/BootNOMP:master](https://github.com/leshacat/BootNOMP) pool is live @ [http://miningpool.easyx.info:44420/](http://miningpool.easyx.info:44420/)
-------

### Helping give NOMP new life! With some style.
***If you want to help contribute, please look at the original [project](https://github.com/foxer666/node-open-mining-portal) first!***

BootNOMP is all the things great about NOMP, now with modern style and design of BootStrap 4! Having disliked the previous UI, due to cramping, little to no info displayed while what is displayed is not very helpful to users. I decided to fork a already great project, and add some stylistic touches it severely needs. I would of considered requesting pulls to the main branch, though with such heavy changes to the project, I decided a hard fork would be well suited. But if you would like to contribute, please consider looking at the [original project](https://github.com/foxer666/node-open-mining-portal) first, as these guys are the ones who helped get this NOMP rebirthing process started.

You can fork this repository by clicking "fork" in the top right.

***Changelog was moved to the bottom!***

-------
### Node Open Mining Portal consists from 3 main modules:
* [BootNOMP](https://github.com/leshacat/BootNOMP.git) - https://github.com/leshacat/BootNOMP.git
* [Stratum Pool](https://github.com/leshacat/node-stratum-pool) - https://github.com/leshacat/node-stratum-pool
* [Node Multihashing](https://github.com/leshacat/node-multi-hashing) - https://github.com/leshacat/node-multi-hashing

_Stratum Pool can be replaced with [node-merged-pool](https://github.com/UNOMP/node-merged-pool) - https://github.com/UNOMP/node-merged-pool._<br>
_Add new algorithms using [Node Multihashing](https://github.com/leshacat/node-multi-hashing) - https://github.com/leshacat/node-multi-hashing._

-------
### !~ DEVELOPMENT WARNING ~!
While the master branch is considered stable, leshacat/BootNOMP is currently under loads of development - check out the development branch (git checkout development)

If you need support, you can join EasyX Community Discord https://discord.gg/vzcbVNW channel #easyx-pool and ask @Shawn for help!

-------
### Requirements
* Node Version Manager (wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash)
* Node 8.1.4 or higher (nvm install v8.1.4)
* Redis Server (sudo apt install -y redis-server)
* Process Manager 2 (npm install -g PM2@latest)
* Coin daemon(s)


-------
### Install
```
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
source ~/.bashrc
nvm install v8.1.4
nvm use v8.1.4
npm update -g
npm install pm2@latest
pm2 init
git clone https://github.com/leshacat/BootNOMP.git
cd BootNOMP
npm install
pm2 start init.js -i max --watch --name pool
```

-------
### Starup
```
pm2 startup
```
Copy & paste the command

-------
### Restarting Pool
```
pm2 stop pool -i max --watch
pm2 start pool -i max --watch
```

-------
### Watching Logs
```
pm2 logs pool
```

-------
### Update
```
cd BootNOMP
git pull
npm update -g
npm --depth 9999 update
pm2 stop pool -i max --watch
pm2 start pool -i max --watch
```

-------
### Run in Docker
_LeshaCat will redo docker as soon as done with block explorer/etc_
1) Correct configs appropriately to your environment in docker directory
2) ```cd docker```
3) ```docker build -t nomp .```
4) ```docker run -d --name nomp -v $(pwd)/config:/opt/config nomp ```

You will need to expose some ports to make it accessible from outside. You can achieve this by adding option -p HOST_PORT:CONTAINER_PORT in 4th step

You can see the logs of the server with ```docker logs -f nomp```, or jump into container with ```docker exec -it nomp```.

-------
### Hashing algorithms
#### Working
|   | Algorithm | Comment|
| ------------- | ------------- | ------------- |
| ✓ | __C11__ | tested shares and payments with Dixicoin |
| ✓ | __Groestl__ | tested only shares with AuroraCoin, blocks not tested |
| ✓ | __lyra2rev2__ | shares work, needs tests with payments. currently being tested with Lunex coin |
| ✓ | __lyra2z__ | Working in testnet *mining* and *payouts* |
| ✓ | __NeoScrypt__ | working now thanks to @foxer666 pushing update to parent repo |
| ✓ | __Qubit__ | Shares works, and blocks should now too. |
| ✓ | __Scrypt__ | tested with AntiLiteCoin, 1CREDIT, ArgusCoin, WAYAWOLFCOIN and many others |
| ✓ | __SHA256__ | tested with VCOIN, don't use with BTC, no Segwit tested |
| ✓ | __X11__ | tested with BrainCoin, CannabisCoin, AdzCoin and many others |
| ✓ | __X16r__ | tested with RavenCoin |
| ✓ | __Yescrypt__ | needs tests, though should work |
| ✓ | __YescryptR16__ | needs tests, though should work |
| ✓ | __YescryptR32__ | currently being tested with WaviCoin. shares work, payments unconfirmed |

#### Need tests
|   | Algorithm | Comment|
| ------------- | ------------- | ------------- |
| ? | __Argon2__ | need tests |
| ? | __Blake__ | need tests |
| ? | __Blake2S__ | need tests |
| ? | __Cryptonight__ | need tests |
| ? | __Dcrypt__ | need tests |
| ? | __Decred__ | need tests |
| ? | __Fresh__ | need tests |
| ? | __Fugue__ | need tests |
| ? | __GroestlMyriad__ | need tests |
| ? | __Quark__ | need tests |
| ? | __Hefty1__ | need tests |
| ? | __Keccak__ | need tests |
| ? | __Lbry__ | need tests |
| ? | __lyra2re__ | need tests |
| ? | __lyra2re2__ | need tests |
| ? | __lyra2z330__ | need tests |
| ? | __NIST5__ | need tests |
| ? | __S3__ | need tests |
| ? | __Scrypt-N__ | need tests |
| ? | __Scrypt-OG__ | need tests |
| ? | __Sha1__ | need tests |
| ? | __SHAvite-3__ | need tests |
| ? | __Skein__ | need tests |
| ? | __X11Ghost__ | need tests |
| ? | __X13__ | need tests |
| ? | __X14__ | need tests |
| ? | __X15__ | need tests |
| ? | __zr5__ | need tests |
| ? | __ziftr__ | need tests |

#### Don't work yet
|   | Algorithm | Comment|
| ------------- | ------------- | ------------- |
| - | __Scrypt-Jane__ | submitblock not working tested with CacheCoin, Yacoin |

-------
### Credits
* [a2hill](//github.com/a2hill) - helped with X16r
* [devnulled](//github.com/devnull-ed) - helped with lyra2z, neoscrypt algo
* [Kris Klosterman / krisklosterman](https://github.com/krisklosterman) - Updated code for work with Node.JS >=8
* [Jerry Brady / mintyfresh68](https://github.com/bluecircle) - got coin-switching fully working and developed proxy-per-algo feature
* [Tony Dobbs](http://anthonydobbs.com) - designs for front-end and created the NOMP logo
* [LucasJones](//github.com/LucasJones) - got p2p block notify working and implemented additional hashing algos
* [UdjinM6](//github.com/UdjinM6) - helped implement fee withdrawal in payment processing
* [Alex Petrov / sysmanalex](https://github.com/sysmanalex) - contributed the pure C block notify script
* [svirusxxx](//github.com/svirusxxx) - sponsored development of MPOS mode
* [icecube45](//github.com/icecube45) - helping out with the repo wiki
* [yoshuki43](//github.com/yoshuki43) - his K-Nomp project has really help the development!
* [leshacat](//github.com/leshacat) - fixed lots of configuration options & block explorer
* Those that contributed to [node-stratum-pool](//github.com/zone117x/node-stratum-pool#credits)

-------
### License
Released under the GNU General Public License v2
http://www.gnu.org/licenses/gpl-2.0.html

-------
### Buy Me Some Coffee?
I drink about 3 pots a day... I will love you forever!


BTC: `1PvSxjrpzNXCuBHCupAGuuzeUe5DE7kB7H`

LTC: `LU6x6qjdMz4btBEhUU1AukJfUNmrwuaJJD`

ETH/ERC20: `0x67a5A070012aBa9dFB50e571A40b3263C258d7D5`

XMR: `88LqrMZhweMGP61EUrHbkqRcxcYuL7fNRG3UrBYW8eGaN19KCjAuM3fTcr5BniFsf2g8Dmi7YVchBBmbHjWdCPkm1axmMUD`

-------
## Changelog
_Entries marked with `*` are considered stable releases._
* v1.1.4 (under development)
   * Forked from 1301313Y by LeshaCat
   * Added Process Manager 2 (pm2@latest)
   * Added coin config files / examples
   * Added donation addresses in config files
   * Added meta tag control in config files
   * Reworked Block Explorer (shows all coins)
   * Fix for https://github.com/foxer666/node-stratum-pool/commit/a07031808059a76a1fc61db9b10099155df1b6bb
   * Fix for https://github.com/foxer666/node-stratum-pool/pull/23/commits/67eace3468a77f7a585303fe8a1a2081eeba4096
   
   
* v1.1.3*
   * Launched website! Be sure to check it out!
   * Redesigned statistics tracking structure, removing redundency.
   * Added more info to the account statistic page.
   * Considered stable, though needs to be fully tested!
   
   
* v1.1.2
   * Change charts once again, to ChartJS
   * Redesigned Pool/Worker stats pages
   * Added Yescrypt R16 & R32 to dependency projects, currently being testing with Wavicoin.
   * Completed more of Dashboard.
   * Added new NavBar
   * Initial Completetion, Almost Ready For Production. Going live @[NotoHash.club](https://notohash.club) soon.
   
   
* v1.1.1
   * Added payment info to redis.
   * Finished initial version of payment history page.
   * Finished initial version of block history page.
   * Finished new homepage.
   * Almost ready for stable release!
   
   
* v1.1.0
    * Added new homepage design.
    * Added dashboard functionality.
    * Added EMA to graphing.
    * Confirmed C11 functionality with Dixicoin.
    
    
* v1.0.9
    * Added pool statistic pages.
    * Expanded API.
    * Cleaned up main nav bar.
    * Added Ravencoin config file.
    
    
* v1.0.8
    * Fixed C11 algorithm.
    * Starting major UI overhaul using BootStrap 4.
    
    
* v1.0.7*
    * Lyra2z (Zcoin) algo fixed, next step is neoscrypt.

