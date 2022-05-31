# 常见问题

**安装过程中途报错怎么办？**

丰盘ECM安装程序一旦进入自动化安装环节，会从DOCKER HUB拉取安装镜像文件，大约500MB，期间比较容易由于网络原因如网速较慢、网络不稳定、断网（Connect failed）、超时（Timeout）等问题导致镜像文件拉取失败。此时可简单的重新运行脚本进行安装即可。如遇到其他问题，可到 [产品反馈站点https://xpan-ekbcloud.canny.io/](https://xpan-ekbcloud.canny.io/) 向我们反馈。

**如何使用我自己公司的HTTPS证书访问丰盘系统？**

在安装阶段选择了开启HTTPS的话，丰盘系统会绑定内置的自颁发的测试证书，可以先通过访问 https://xpan.local/app/ 访问系统（注意，请先通过hosts修改xpan.local域名指向部署的主机IP），如果提示证书不安全，说明HTTPS初始配置是正确的。

然后登录丰盘系统所在主机，访问丰盘工作目录下的证书目录 **cd /opt/xpan/data/secrets/** `，然后将贵公司的HTTPS证书（针对nginx的）的key和crt后缀的两个文件，更名之后替换掉证书目录下的同后缀文件，然后运行`` `**`docker restart xpan-gw`**` ``命令重启丰盘系统网关，使用贵公司的HTTPS域名访问丰盘系统即可。`

**系统安装完成之后可以修改端口配置吗？**

可以的，在丰盘系统安装完之后会自带一个CLI管理工具，存放在 /opt/xpan/tools/ 目录下，可以运行如下命令重新进入端口配置界面：

```bash
cd /opt/xpan/tools/
sudo ./xpc.sh config port
```

``

``
