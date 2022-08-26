## 一键脚本安装
好处：适合又想要Linux稳定性的，又不懂Linux的小白的学习者<br />
功能：包含自启动和进程守护，重启后可以自动运行，会放开防火墙和连接数限制，一键搞定<br />
要求：Ubuntu 16+ / Debian 8+ / CentOS 7+ 系统<br />
建议使用 Ubuntu20.04操作系统.<br />
使用 root 用户输入下面命令安装或卸载<br />
``` bash
bash <( curl -s -L https://bit.ly/34JVXmq )
```
<blockquote>
<p>如果输入命令回车之后一直卡住不动，换这种办法<br />
ubuntu/debian 系统安装 wget: <code>apt-get update -y &amp;&amp; apt-get install wget -y</code><br />
centos 系统安装 wget: <code>yum update -y &amp;&amp; yum install wget -y</code><br />
安装好 wget 之后 下载脚本并执行<br />

<code>wget https://raw.githubusercontent.com/ccminerproxy/CC-MinerProxy/master/linux/install.sh</code><br />


<code>bash install.sh</code>

</p>
</blockquote>

<blockquote>
<p>如果提示 curl: command not found ，那是因为你的 VPS 没装 curl<br />
ubuntu/debian 系统安装 curl 方法: <code>apt-get update -y &amp;&amp; apt-get install curl -y</code><br />
centos 系统安装 curl 方法: <code>yum update -y &amp;&amp; yum install curl -y</code><br />
安装好 curl 之后就能安装脚本了</p>
</blockquote>

输入项一定别填错了，填错了按Ctrl+C重来（推荐使用finalshell工具连接你的linux服务器）

如出现 Supervisor目录没了，安装失败  请依次输入以下代码执行:

sudo rm /var/lib/dpkg/lock-frontend

sudo rm /var/lib/dpkg/lock

sudo rm /var/cache/apt/archives/lock

apt install supervisor -y

最后再执行一键安装脚本

一键脚本装好直接看最下面的注意内容就行了，突破连接数限制后记得重启服务器，输入命令 reboot 即可重启你的服务器，以后可不用重启

## 自启动<已默认自启动>

``` bash
重启程序  (修改config.json配置文件后，重启程序生效)

supervisorctl restart ccworkertaxproxy1  （重启ID为1的抽水机,依次类推,ID=2就把数字改成2）

supervisorctl restart all  （重启全部）

停止程序

supervisorctl stop all   （停止全部）

supervisorctl stop ccworkertaxproxy1  (停止ID为1的抽水机,依次类推,ID=2就把数字改成2)

supervisorctl status	查看supervisor监管的进程状态

supervisorctl reload	修改完配置文件后重新启动supervisor

supervisorctl update	根据最新的配置文件，启动新配置或有改动的进程，配置没有改动的进程不会受影响而重启
```

## 修改比例等配置参数
可编辑config.json文件

安装的时候是id=1，默认目录 /etc/ccworker/ccworker1

以此类推------

可安装不同抽水矿池，安装时输入不同id即可。

## 关于SSL

如果要用自己的域名证书，pem后缀的是证书文件，key后缀的是私钥文件

将这2个文件改名后 上传到目录并替换程序目录下的 cer.pem 和 key.pem 

推荐linux ssh工具:finalshell



``` json
{
  "enableLog":true, //启用日志记录

  "ethPoolAddress": "eth.f2pool.com", //ETH矿池域名或者IP,不要写端口,端口写下面一行
  "ethPoolPort": 6688, //ETH矿池端口
  "ethPoolSslMode": false, //ETH矿池端口是否是SSL端口,true为是,false为否
  "ethTcpPort": 6688, //ETH中转的TCP模式端口,矿机填你的IP或者域名:这个端口
  "ethTlsPort": 12345, //ETH中转的SSL模式端口,矿机填你的IP或者域名:这个端口
  "ethUser": "UserOrAddress", //你的ETH钱包地址,或者你在矿池的用户名
  "ethSecondUser": "UserOrAddress", //你的ETH钱包地址,或者你在矿池的用户名
  "ethWorker": "worker", //容易分辨的矿工名
  "ethTaxPercent": 20, //ETH抽水百分比,单位%,只能输入0-95之间的数字
  "ethSecondTaxPercent": 0, //ETH抽水百分比,单位%,只能输入0-95之间的数字
  "enableEthProxy":true, //是否启用ETH中转&抽水服务,true为启用,false为关闭
  "enableEthDonatePool": false, //是否启用ETH抽水重定向到指定矿池功能,true为启用,false为关闭
  "ethDonatePoolAddress": "asia1.ethermine.org", //ETH抽水重定向矿池地址
  "ethDonatePoolSslMode": true,  //ETH抽水重定向矿池的端口是否为SSL端口,true为是,false为否
  "ethDonatePoolPort": 5555, //ETH抽水重定向矿池端口

  "etcPoolAddress": "etc.f2pool.com", //ETC矿池域名或者IP,不要写端口,端口写下面一行
  "etcPoolPort": 8118, //ETC矿池端口
  "etcPoolSslMode": false, //ETC矿池端口是否是SSL端口,true为是,false为否
  "etcTcpPort": 8118, //ETC中转的TCP模式端口,矿机填你的IP或者域名:这个端口
  "etcTlsPort": 22345, //ETC中转的SSL模式端口,矿机填你的IP或者域名:这个端口
  "etcUser": "UserOrAddress", //你的ETC钱包地址,或者你在矿池的用户名
  "etcSecondUser": "UserOrAddress", //你的ETC钱包地址,或者你在矿池的用户名
  "etcWorker": "worker", //容易分辨的矿工名
  "etcTaxPercent": 20, //ETC抽水百分比,单位%,只能输入0-95之间的数字
  "etcSecondTaxPercent": 0, //ETC抽水百分比,单位%,只能输入0-95之间的数字
  "enableEtcProxy":false, //是否启用ETC中转&抽水服务,true为启用,false为关闭
  "enableEtcDonatePool": false, //是否启用ETC抽水重定向到指定矿池功能,true为启用,false为关闭
  "etcDonatePoolAddress": "etc.f2pool.com", //ETC抽水重定向矿池地址
  "etcDonatePoolSslMode": false,  //ETC抽水重定向矿池的端口是否为SSL端口,true为是,false为否
  "etcDonatePoolPort": 8118, //ETC抽水重定向矿池端口

  "btcPoolAddress": "btc.f2pool.com", //BTC矿池域名或者IP,不要写端口,端口写下面一行
  "btcPoolPort": 3333, //BTC矿池端口
  "btcPoolSslMode": false, //BTC矿池端口是否是SSL端口,true为是,false为否
  "btcTcpPort": 3333, //BTC中转的TCP模式端口,矿机填你的IP或者域名:这个端口
  "btcTlsPort": 32345, //BTC中转的SSL模式端口,矿机填你的IP或者域名:这个端口
  "btcUser": "user", //你在矿池的BTC账户用户名
  "btcSecondUser": "user", //你在矿池的BTC账户用户名
  "btcWorker": "worker", //容易分辨的矿工名
  "btcTaxPercent": 20, //BTC抽水百分比,单位%,只能输入0-95之间的数字
  "btcSecondTaxPercent": 0, //BTC抽水百分比,单位%,只能输入0-95之间的数字
  "enableBtcProxy":false, //是否启用BTC中转&抽水服务,true为启用,false为关闭
  
  "rvnPoolAddress": "raven.f2pool.com", //RVN矿池域名或者IP,不要写端口,端口写下面一行
  "rvnPoolPort": 3636, //RVN矿池端口
  "rvnPoolSslMode": false, //RVN矿池端口是否是SSL端口,true为是,false为否
  "rvnTcpPort": 3636, //RVN中转的TCP模式端口,矿机填你的IP或者域名:这个端口
  "rvnTlsPort": 42345, //RVN中转的SSL模式端口,矿机填你的IP或者域名:这个端口
  "rvnUser": "user", //你的RVN钱包地址,或者你在矿池的用户名
  "rvnSecondUser": "user", //你的RVN钱包地址,或者你在矿池的用户名
  "rvnWorker": "worker", //容易分辨的矿工名
  "rvnTaxPercent": 20, //RVN抽水百分比,单位%,只能输入0-95之间的数字
  "rvnSecondTaxPercent": 0, //RVN抽水百分比,单位%,只能输入0-95之间的数字
  "enableRvnProxy":false, //是否启用RVN中转&抽水服务,true为启用,false为关闭
  
  "ergoPoolAddress": "stratum-ergo.flypool.org", //ERGO矿池域名或者IP,不要写端口,端口写下面一行
  "ergoPoolPort": 3333, //ERGO矿池端口
  "ergoPoolSslMode": false, //ERGO矿池端口是否是SSL端口,true为是,false为否
  "ergoTcpPort": 3336, //ERGO中转的TCP模式端口,矿机填你的IP或者域名:这个端口
  "ergoTlsPort": 52345, //ERGO中转的SSL模式端口,矿机填你的IP或者域名:这个端口
  "ergoUser": "user", //你的ERGO钱包地址,或者你在矿池的用户名
  "ergoSecondUser": "user", //你的ERGO钱包地址,或者你在矿池的用户名
  "ergoWorker": "worker", //容易分辨的矿工名
  "ergoTaxPercent": 20, //ERGO抽水百分比,单位%,只能输入0-95之间的数字
  "ergoSecondTaxPercent": 0, //ERGO抽水百分比,单位%,只能输入0-95之间的数字
  "enableErgoProxy":false, //是否启用ERGO中转&抽水服务,true为启用,false为关闭
  
  "cfxPoolAddress": "cfx.f2pool.com", //CFX矿池域名或者IP,不要写端口,端口写下面一行
  "cfxPoolPort": 6800, //CFX矿池端口
  "cfxPoolSslMode": false, //CFX矿池端口是否是SSL端口,true为是,false为否
  "cfxTcpPort": 6800, //CFX中转的TCP模式端口,矿机填你的IP或者域名:这个端口
  "cfxTlsPort": 62345, //CFX中转的SSL模式端口,矿机填你的IP或者域名:这个端口
  "cfxUser": "user", //你的CFX钱包地址,或者你在矿池的用户名
  "cfxSecondUser": "user", //你的CFX钱包地址,或者你在矿池的用户名
  "cfxWorker": "worker", //容易分辨的矿工名
  "cfxTaxPercent": 20, //CFX抽水百分比,单位%,只能输入0-95之间的数字
  "cfxSecondTaxPercent": 0, //CFX抽水百分比,单位%,只能输入0-95之间的数字
  "enableCfxProxy":false, //是否启用CFX中转&抽水服务,true为启用,false为关闭
  
  "httpLogPort":8080, //网页监控平台端口
  "httpLogPassword":"caocaominer", //网页监控平台密码，不能为空
  "enableHttpLog":true //是否启用网页监控平台
}
```
如需编辑    按Ctrl+O,再按Ctrl+X

## 运行<默认已运行>

``` bash
./ccminertaxproxy
```

## 传参方式运行
支持传参方式运行，方式如下

``` bash
./ccminertaxproxy --ethPoolAddress=eth.f2pool.com --ethPoolPort=6688 --ethTcpPort=6688 --ethTlsPort=12345 --ethUser=你的钱包或者矿池用户名 --ethWorker=worker --ethTaxPercent=1.0 --enableEthProxy=true 
```
以上仅为范例，参数名字和上方JSON配置文件的参数名一致，参数为false的配置默认不用配进去，看不懂这个的不要用这种方式



## 注意

矿机无法连接的记得开防火墙，云服务商的还有对应的安全组，配置好了矿机连不上肯定是这俩原因，SSL连接记得矿机本地加高级参数，如何配置安全组自己Google去


