## Todesk远程开关电脑

</br>

远程软件比较常见的就是TeamViewer了，还有向日葵，不是说这些软件不好(以免遭黑)，个人体验下来，Todesk稳定不掉线，流畅度上都很不错

本次只演示

* 手机远程关机

* 手机远程开机

* 额外：Linux安装Tosesk并远程



## 手机远程关机


PC端安装Tosesk

官网：https://www.todesk.com/

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-01.png)


支持电脑、手机甚至支持linux

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-02.png)


安装、注册好账号，并登录

> 修改密码在网页端可以改

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-03.png)



手机端安装好todesk，并登录同样的账号

填入`远程设备代码`  点击远程控制，填入`临时密码`即可远程桌面

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-04.png)


远程成功后，就可以操作电脑了，单击、双击命令说明里面也有

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-05.png)

</br>

怎么关机就不用说了吧

</br>
</br>


## 手机远程开机

</br>

个人建议：如无必要，不建议折腾，选个智能插座就可以了


</br>

注意：下列演示，需要的条件非常多，todesk远程唤醒还需要有同一局域网的设备(电脑或手机)

原理：A手机(外地) → 远程B安卓机(同一wifi) → 远程开机电脑(同一wifi)；A手机 → 远程电脑

> 苹果无法远程控制，被控制手机必须安卓


</br>

就是这么的复杂，基本上可以劝退大部分人了

</br>

### 1.A手机的设置

建立一次电脑连接后

在我的-设置-打开 `Wake 0n Lan` 开关

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-06.png)



</br>


### 2.B手机的设置


登录同一账号，开启`允许远程本设备`- 控制模式 - 开启所有开关-开启被控模式


![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-07.png)

在我的-设置-打开 `Wake 0n Lan` 开关

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-08.png)


然后A手机连接一次B手机，是否能正常连接，确认可以后断开


</br>


### 3.电脑设置

请保持B手机和电脑在同一WIFI下，[详情请参考Todesk文档：远程开机如何配置 Wake On Lan](https://www.todesk.com/helpcenter/questions-86.html)

</br>

**3.1 网卡设置**

我的电脑-右键-属性-设备管理器

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-09.png)

网络适配器，找到网卡-右键-属性，我这里是 `Realtek...Controller`

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-10.png)


电源管理 选项卡里面开启 `允许此设备唤醒计算机`

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-11.png)



然后在 高级 选项卡里找到`wake on magic packet`、`关机网络唤醒`、`魔术封包唤醒`里设置成**开启**

`网络唤醒和关机连接速度`，改成 100Mbps 优先，确定！一定要点确定生效！

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-12.png)


</br>

**3.2 设置主板BIOS**

需要在主板 BIOS 里面设置 WOL 唤醒功能的开关

```
不同主板 BIOS 里关于 WOL 网络唤醒的选项一般是类似这些字眼:
wake on lan；
resume on lan；
power on PME；
power on by PCI-E device;
Power on by Onboard LAN
等等，将其设为 Enabled 即可
```

我以我的 微星msi主板演示，只是演示！其他根据自己的主板来！

重启按`DEL`键进入BIOS，SETTINGS-Advanced

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-13.png)


再进入 Wake Up Event Setup

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-14.png)


将 Resume By PCI-E Device 改成 `Enabled`，按 `F10` 保存并推出

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-15.png)

</br>

**3.3 路由器进行ARP绑定**


</br>

我是斐讯路由器，浏览器`192.168.2.1`进入路由器，其他路由大部分是`192.168.1.1`


功能设置-DCHP服务-绑定，这样即便重启了地址也不会变

> 其他路由器自己找下，只要把MAC地址和IP绑定即可

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-16.png)


</br>


### 4.开机

</br>

所有设置都完成了，我们关掉电脑。A手机用数据打开Tosesk-设备列表-远程B安卓手机，安卓机也打开Tosesk-设备列表-远程开机电脑

> B手机要和电脑在同一WIFI下哦

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-17.png)

电脑已进入开机界面，完结

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-18.png)



</br>
</br>



## 额外：Linux安装Tosesk并远程


</br>

由于系统原因，需要有图形界面的系统才可安装，我这里以Centos为例


[不会切换图形界面的☛点我教程：centos系统切换图形界面](https://github.com/Yiov/notes/tree/main/Centos)


我们进入Centos后，打开todesk官网下载Linux版本

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-19.png)


我这里用的是Centos，下载Centos7即可

> 其他版本按自己的系统下载

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-20.png)


下载后我们把下载的文件，放到`主目录`才可以正确安装！否则会提示找不到文件！

> 找不到的看我图示，就是和公共、视频、图片等同一级目录

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-21.png)


然后我们看 [官方文档](https://www.todesk.com/linux.html) ，输入安装命令


注意：请把这里安装包名改对，不然也安装不了

> 自己下的包名是什么，这里就填什么，少一个字都不行!

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-22.png)


在桌面-鼠标右键-打开终端，输入命令，等待安装完成

```
sudo rpm -Uvh todesk-v4.3.1.0-c7-x86_64.rpm
```

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-23.png)

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-24.png)



然后启动todesk，安装好登录账号就可以用了

```
todesk
```
![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-25.png)

![](https://ghproxy.com/https://raw.githubusercontent.com/Yiov/notes/main/todesk/todesk-26.png)


</br>
</br>


### 常见问题

</br>

1.能正常使用

```
sudo systemctl stop todeskd.service
sudo mv /opt/todesk/config/config.ini /opt/todesk/config/config.ini.bak
sudo systemctl start todeskd.service
```

</br>

2.错误日志

查看服务日志：（例如:xxxx_xx_xx.log为2022_08_03.log）

```
tail -f /var/log/todesk/service_xxxx_xx_xx.log
```

查看客户端日志：（例如:xxxx_xx_xx.log为2022_08_03.log）

```
tail -f ~/.local/share/todesk/Logs/client_xxxx_xx_xx.log
```

</br>


3.删除服务设置配置

```
sudo rm /opt/todesk/config/config.ini
```

</br>

4.卸载:

```
rpm -e todesk
```


</br>
</br>



## 特别鸣谢

</br>

* [ToDesk](https://www.todesk.com/)

* [TeamViewer](https://www.teamviewer.cn/cn/)

* [向日葵](https://sunlogin.oray.com/)




