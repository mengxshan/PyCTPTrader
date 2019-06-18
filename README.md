# PyCTPTrader

本项目是在[PyCTP](https://github.com/xystcz/PyCTP)基础上(原[PyCTP](https://github.com/shizhuolin/PyCTP)看穿式监管版本在linux下存在编译问题，因此fork一个新分支)，对Python接口做进一步封装，
自动处理了所有的回调函数，无需再次重写

简化了下单撤单流程，可直接从Python对象获取每一笔交易的实时状态

添加对看穿式监管版本的支持

## 环境配置

基于Python3环境， 并在此基础上安装扩展: [PyCTP](https://github.com/xystcz/PyCTP)

IDE建议使用Pycharm

## 代码配置

Sample目录下有样例代码，运行前需要配置好ctp.json文件，具体配置方式如下：

```
cfg:    配置文件路径，一般以ctp.json命名，每个账户对应如下配置项，以上期模拟账户为例：
        "simnow": {                           # 账户名称
            "TraderFront": [                   # 交易服务器，可以配置多个，程序自动选择可用服务器
                "tcp://180.168.146.187:10001",
                "tcp://180.168.146.187:10000",
                "tcp://218.202.237.33 :10002"
            ],
            "TraderCache": "_tmp_simnow_t_",    # 交易api缓存，仅包含字母和下划线，每个账户的缓存名称需保持唯一
            "MarketFront": [                    # 行情服务器，可以配置多个，程序自动选择可用服务器
                "tcp://180.168.146.187:10011",
                "tcp://180.168.146.187:10010",
                "tcp://218.202.237.33 :10012"
            ],
            "MarketCache": "_tmp_simnow_m_",    # 行情api缓存，仅包含字母和下划线，每个账户的缓存名称需保持唯一
            "Broker": "9999",                   # 期货公司代码
            "User": "76871313",                 # 账号
            "Password": "5746531"               # 密码
            "Client": "SHINNYQ7V2",             # 客户端名称，看穿式监管验证必须填写
            "AuthCode": "ASDFAFASDFASFA"        # 客户端校验码，看穿式监管验证必须填写
        }
```
