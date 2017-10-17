## 1. 环境介绍
* 服务器：ubuntu 16.04
* 客户端：win10、ubuntu 16.04桌面版
* 浏览器：chrome、firefox

## 2. 服务器的购买
1. 按需选择合适自己的服务器提供商。我知道的有两个VPS的提供商：[DigitalOcean](https://www.digitalocean.com/github-students/?utm_medium=partnerships&utm_source=github&utm_campaign=studentdevpack)和[搬瓦工](http://banwagong.cn/)。我因为个人身份以及只有自己一个人的原因选择了前者，因此该文是基于DO来介绍的。<br/>
2. 打开上述链接，貌似注册成功会送$10，但是我没有收到...，按照提示一步步的进行。**注意**：注册过程中为了恶意注册，必须充值$5，付款方式使用paypal，没有就[注册](https://www.paypal.com/c2/webapps/mpp/consumer?locale.x=zh_C2)，以后说不定也能用到。我选择的主机是最低配置的ubuntu 16.04，服务器在洛杉矶，自己目前的使用感受感觉挺快，视频可以流畅的观看，就是不知道是不是没有配置好，有时连不上。**注意**：在购买主机时，最后勾选上SSH，这样更加安全，不会可以按照提示走。然后你就拥有了一个属于自己的服务器，离科学上网就差一点了。
3. 另外如果你拥有.edu.cn结尾的邮箱，可以使用[GitHub Student Pack](https://education.github.com/)，得到$50，这样理想情况下，你将拥有$65，可以使用最低配置的主机13个月，是不是性价比很高。当然如果没有以上的条件，还是搬瓦工性价比最高，这点是很多人认同的。

## 3. ss服务器端的搭建
1. 直接在DO上登录主机，我因为总是登不上网站，所有在WIN10上使用XShell连接上的主机。也有不少人推荐使用putty，这个我没有用过，感觉XShell还是挺好用的，虽然界面有点丑...
2. 下面开始安装SS并进行配置了：<br/>
* 更新源和本地包
`
sudo apt-get update
sudo apt-get upgrade
`
* 安装python，安装过就不用了
`
sudo apt-get install python
`
* 安装pip并更新
`
sudo apt-get install python-pip
sudo install --upgrade pip
`
* 安装ss
`
sudo pip install shadowsocks
`
* 配置ss，位置可以自己选择
`
vim /etc/shadowsocks.json
`
```bash
{
"server":"::",
"timeout":300,
"port_password":{
"100000":"your password1",
"100001":"your password2",
"100002":"your password3"
},
"local_port":1080,
"method":"aes-256-cfb",
"fast_open":true,
"workers":1
}
```
其中：
`server`是服务器的IP地址；
`timeout`是最长连接时间延迟；
`port_password`用来设置多个端口以及对应密码；
`local_port`是本地端口，可以不用管；
`method`是传输的加密方式；
`fast_open`可能提高速度，ubuntu系统中建议使用；
`workers`这个暂时没有多做了解，不太懂时就这样填即可。

* 启动ss，使得刚才的配置生效
`
sudo ssserver -c /etc/shadowsocks.json -d start
`
*关闭*
`
sudo ssserver -c /etc/shadowsocks.json -d stop
`
*重启，修改json文件后*
`
sudo ssserver -c /etc/shadowsocks.json -d restart
`
