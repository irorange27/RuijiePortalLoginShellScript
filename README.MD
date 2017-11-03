# 简介

本脚本实现了锐捷 ePortal Web 认证的登录，需要 curl 指令的支持，通过 curl 发送认证所需的 POST 数据包来实现 Web 认证。

# 用法

```shell
chmod +x ruijie.sh
./ruijie.sh interface username password
```

- interface参数为锐捷认证的宽带接入参数，可以为chinanet（电信宽带接入）、chinamobile（移动宽带接入）、chinaunicom（联通宽带接入）或者为campus（教育网接入）。这个参数仅仅适用于我所在的大学，如果你想将本脚本用于你的大学需要做相应的修改。
- username参数为认证用户名。
- password参数为认证密码。

# 局限性

在锐捷 ePortal Web 认证的 POST 数据包中发现了 validcode 参数，根据名字猜测这个参数应该是验证码。

我所在的学校并没有开启验证码，如果你的学校在登录的时候需要验证码，那么本脚本将无法进行认证。

同时本脚本代码编写的很乱，工作效率不高。

# 吐槽

锐捷的 ePortal Web 认证上了之后，向 InterFace.do?method=getOnlineUserInfo 这个接口中 Post 过去 userIndex 参数会明文显示用户的密码，感觉一点安全性都没有。

以及，我所在的学校在未认证的情况下，53端口(DNS)是可以正常通信的，可以尝试搭建个53端口的代理实现免认证上网（未测试，不保证能成功）。