# aws_shadowsocks
aws_shadowsocks科学上网

## aws ec2 12月免费试用
aws提供12月的免费vps免费试用，直接去[AWS官网](https://aws.amazon.com/cn/)创建免费账户试用即可。

申请需要有可用的双币信用卡，过程中会刷一笔 $1 USD 的预授权，目的是验证信用卡可用，钱不是aws收走的

### 启动 ec2 实例(instance)
1. 用之前注册的aws免费账户登录[控制台](console.aws.amazon.com)，右上角选择机房位置。美国机房速度较慢，可选东京。但如果选东京，部署的shadowsocks ip也为日本，科学上网使用google/youtube等时，均默认日本网页。如果觉得不能忍，就还是用美国机房吧

2. 在aws控制台中，选择EC2，启动实例，选择Amazon Linux AMI->t2.micro(重要！small以上的不免费)，然后一路next。在最后提示需要“选择现有密钥对或创建新密钥对”时，选择差u你关键新的，然后随意命名(但也别太随意，以免后来忘记，如aws_ec2_tokoy_test)，选择下载并保存到本地

3. 绑定ip地址。依旧在控制台，左边栏“网络与安全”下，点击“弹性ip”，选择“分配新地址”，然后就获得了一个固定ip，这个ip以后将作为登陆aws虚拟机的地址和shadowsocks服务器ip。分配完成后，选中刚才分配的ip，点击“操作”->“关联地址”，选择刚才启动的实例即可。

## shadowsocks配置
1. ssh登陆aws虚拟机: 依旧在aws EC2 控制控制台下，点击“连接”，按照提示，修改刚才下载到本地的密钥对文件权限。然后 ssh 连接即可
2. 安装shadowsocks：登陆虚拟机后，按照如下安装shadowsocks
``` shell
$ wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh 
$ chmod +x shadowsocks.sh
$ sudo ./shadowsocks.sh 2>&1 | tee shadowsocks.log
```
如果提示 `https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh` 无法访问(404)，直接去[Teddysun/shadowsocks_install
](https://github.com/teddysun/shadowsocks_install/) 找 `shadowsocks.sh` 的url，替换上面即可
3. 
### aws服务器端
### windows客户端

## firefox+fireproxy