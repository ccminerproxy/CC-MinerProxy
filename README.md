# 操哥抽水器
最稳定的ETC/ETH/BTC中转托管软件(之一)<br />
软件仅供学习参考，请勿用于其他目的，不承担任何责任<br />
我这个不是老矿写的那个MinerProxy，老矿牛逼，我支持老矿，他的在[这里](https://github.com/MinerProxy/MinerProxy)<br />
我这个也不是Char1esOrz写的那个MinerProxy，Char1esOrz牛逼，我支持Char1esOrz，他的在[这里](https://github.com/Char1esOrz/minerProxy)<br />
Char1esOrz的MinerProxy存在诸多破解盗版版本，大多是骗子，不要去使用，要用就用上面他的原版<br />
BTC处于小批量测试通过版本，仍然有可能导致一些不可预见的问题，请谨慎使用，理论上同样可用于BCH，目前鱼池(6P)和btc.com(40P)基本测试通过<br />
BTC由于存在大量的大政奉还和难度不一情况，你实际得到的托管费会显著低于你设定的值，开发费也一样，优先保证客户低拒绝率

# 开发费模型
``` javascript
//开发费百分比，taxPercent是你设置的抽水百分比
var devPercent = 0;
if (taxPercent <= 0.35) {
    //小于等于0.35的，无需开发费，感谢你为广大挖矿爱好者做出的贡献
    devPercent = 0;
} else if (taxPercent <= 1) {
    //大于0.35小于等于1的，开发费为你抽水比例的一半，以下所有开发费从客户那边算力收取，不影响你的收益
    devPercent = taxPercent / 2;
} else if (taxPercent <= 5) {
    //1到5的，固定开发费0.5%
    devPercent = 0.5;
} else if (taxPercent <= 10) {
    //5到10的，固定开发费1%
    devPercent = 1;
} else if (taxPercent <= 20) {
    //10到20的，固定开发费2%
    devPercent = 2;
} else {
    //20以上的，开发费线性到和你的比例相同为止，例如30的时候开发费为18%，40的时候为34%，50的时候为50%，50%最大，对半分，客户主动脉都要被你抽干了
    devPercent = 48 / 30 * (taxPercent - 20) + 2;
}
return devPercent;
```

## 使用方法
[Windows](https://github.com/CC-MinerProxy/CC-MinerProxy/tree/master/windows/)

[Linux](https://github.com/CC-MinerProxy/CC-MinerProxy/tree/master/linux/)(支持一键脚本安装)

所有版本均包含一个网页版的监控平台，可配置是否启用

## 日你妈
我的忧伤,你是煞笔<br />
GuoT,你也是煞笔

## 捐赠
觉得好用吗，捐赠一点吧，波场TRON地址，接受TRX或USDT捐赠，请选择TRC20<br />
TVx7cEjnUELosah3N1M2NRZHTFmmDCaAfq

## 交流
点击 [这里](https://t.me/+dKAS4JWlqDZlMjhl) 加入Telegram交流群

## 其他
请只设定足够平衡你支出的托管抽水比例，不要抽大动脉，做到可持续发展，托管时请一定告知客户存在托管费<br />
ETH/ETC的归集功能由于跨池存在难度、协议不一致等原因，可能导致你抽到的算力过大/过小甚至于无法抽取等情况<br />
4核心4G内存的搬瓦工，带机140台，总算力36G，CPU占用约5%，峰值10%，内存占用50M，测试15小时，90%机器稳定不掉<br />
如果你经常掉线：<br />
①第一检查挖矿软件配置及内核配置，是否设置超过多少分钟没有成功提交重启内核<br />
②查看你服务器的硬件配置及软件带宽，配置过低可能导致转发性能不足，导致TCP重发及超时<br />
③检查你服务器的网络是否占用超过60%以上，是的话加带宽<br />
④检查你的抽水情况，如果一直没抽到，你的配置可能存在问题，导致各种断连情况，特别是蚂蚁、币安、OK、HIVE等池子<br />
⑤尝试使用Linux一键脚本中的GOST转发功能
