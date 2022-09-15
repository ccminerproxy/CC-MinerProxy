## 下载

目录里的文件都要下载

## 运行方式①

打开CaoMinerTaxProxy.exe，记得关闭杀毒软件，不然可能误报
打开后几个配置自己配置，配置完了点击启动
每次启动系统都要重新运行一次

## 运行方式②

自行编辑config.json文件，注意//之后的都删掉，包括//
``` json
{
  "enableLog":true, //启用日志记录

  "ethPoolAddress": "ethw.f2pool.com", //ETHW/ETF矿池域名或者IP,不要写端口,端口写下面一行
  "ethPoolPort": 6688, //ETHW/ETF矿池端口
  "ethPoolSslMode": false, //ETHW/ETF矿池端口是否是SSL端口,true为是,false为否
  "ethTcpPort": 6688, //ETHW/ETF中转的TCP模式端口,矿机填你的IP或者域名:这个端口
  "ethTlsPort": 12345, //ETHW/ETF中转的SSL模式端口,矿机填你的IP或者域名:这个端口
  "ethUser": "UserOrAddress", //你的ETHW/ETF钱包地址,或者你在矿池的用户名
  "ethSecondUser": "UserOrAddress", //你的ETHW/ETF钱包地址,或者你在矿池的用户名
  "ethWorker": "worker", //容易分辨的矿工名
  "ethTaxPercent": 20, //ETHW/ETF抽水百分比,单位%,只能输入0-95之间的数字
  "ethSecondTaxPercent": 0, //ETHW/ETF抽水百分比,单位%,只能输入0-95之间的数字
  "enableEthProxy":true, //是否启用ETHW/ETF中转&抽水服务,true为启用,false为关闭
  "enableEthDonatePool": false, //是否启用ETHW/ETF抽水重定向到指定矿池功能,true为启用,false为关闭
  "ethDonatePoolAddress": "asia1.ethermine.org", //ETHW/ETF抽水重定向矿池地址
  "ethDonatePoolSslMode": true,  //ETHW/ETF抽水重定向矿池的端口是否为SSL端口,true为是,false为否
  "ethDonatePoolPort": 5555, //ETHW/ETF抽水重定向矿池端口

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

编辑好config.json文件,或者用CaoCaoMinerTaxProxy.exe配置好运行一次
管理员权限打开命令行cmd
切换到本目录

输入nssm install CMinerProxy
点击Path后面的省略号，选择ccminertaxproxy.exe
点击Install service
重启系统即可自动启动


## 传参方式运行
支持传参方式运行，方式如下

``` command
ccminertaxproxy.exe --ethPoolAddress=eth.f2pool.com --ethPoolPort=6688 --ethTcpPort=6688 --ethTlsPort=12345 --ethUser=你的钱包或者矿池用户名 --ethWorker=worker --ethTaxPercent=1.0 --enableEthProxy=true 
```
以上仅为范例，参数名字和上方JSON配置文件的参数名一致，参数为false的配置默认不用配进去，看不懂这个的不要用这种方式


## 注意

千万不要忘记修改配置文件
千万不要忘记修改配置文件
千万不要忘记修改配置文件

如修改了配置，修改后需要重新执行程序，或者去services.msc里重启CMinerProxy服务

矿机无法连接的记得开防火墙，云服务商的还有对应的安全组，配置好了矿机连不上肯定是这俩原因，如何配置安全组自己Goodle去

需要增加TCP连接数，[查看这里](https://m.kafan.cn/A/pv06e54mvd.html)


## 关于SSL

如果要用自己的域名证书，请直接替换key.pem和cer.pem文件，如果看不懂这句话就不要管，凤凰不用自己的域名证书无法使用SSL模式
