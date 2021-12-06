## 安装
``` bash
apt update 
apt install git -y
mkdir /opt
cd /opt
git clone https://github.com/CaoCaoMiner/CC-Miner-Tax-Proxy.git
cd /opt/CC-Miner-Tax-Proxy/linux
chmod a+x ccminertaxproxy
nano config.json
```
编辑好后按Ctrl+O,再按Ctrl+X


## 编辑配置

自行编辑config.json文件
``` json
{
  "poolAddress": "eth.f2pool.com",//矿池域名或者IP
  "poolPort": 6688,//矿池端口
  "tcpPort": 6688,//中转的TCP模式端口
  "tlsPort": 12345,//中转的SSL模式端口
  "user": "你的钱包地址",//你的钱包地址，或者你在矿池的用户名
  "worker": "矿工地址",//容易分辨的矿工名
  "taxPercent": 0.35//抽水百分比，单位%，只能输入0.3-20之间的数字
}
```

## 运行

``` bash
./ccminertaxproxy
```

## 自启动

``` bash
apt install supervisor -y
cd /etc/supervisor/conf/
nano ccminer.conf
```
```
[program:ccminertaxproxy]
command=/opt/CC-Miner-Tax-Proxy/linux/ccminertaxproxy
directory=/opt/CC-Miner-Tax-Proxy/linux/
autostart=true
autorestart=true
```
``` bash
supervisorctl reload
```

## 关于SSL

如果要用自己的证书，请直接替换key.key和cer.crt文件，如果看不懂这句话就不要管