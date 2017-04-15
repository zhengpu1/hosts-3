## dnsmasq规则文件说明：
* dnsad：屏蔽广告家族
* dnsfq：翻墙专用，这个需要大家共同努力完善。
* dnsip：屏蔽运营商劫持与一些广告IP（如何查看是否被劫持，输入nslookup baiduiiii.com，若返回IP就是劫持，请把那个IP发给我）
* hosts：默认使用的是vokins的完整AD hosts。如PC需看视频的，请自行更换为不带屏蔽视频广告的hosts.txt规则，https://raw.githubusercontent.com/vokins/yhosts/master/hosts.txt


## 手动修改教程：
此方法适用于openwrt类的路由器，来自机友https://www.mylede.cf/?p=125 

使用脚本前请检查dnsmasq.conf的配置。/etc/dnsmasq.conf 看是否有conf-dir 配置参数，默认貌似是没有的。添加conf-dir=/etc/dnsmasq.d.会自动加载目录下的配置文件。

### 然后执行以下命令即可：
* wget -q https://raw.githubusercontent.com/sy618/hosts/master/dnsmasq/dnsfq -O /etc/dnsmasq.d/gfw.conf –no-check-certificate ; /etc/init.d/dnsmasq restart

### 如果想定时执行，请在网页配置端的计划任务添加以下脚本：
* 01 06 * * * wget -q https://raw.githubusercontent.com/sy618/hosts/master/dnsmasq/dnsfq -O /etc/dnsmasq.d/gfw.conf –no-check-certificate ; /etc/init.d/dnsmasq restart
```javascript
* 注：不同路由器固件可能文件位置不一样
```







## 【华硕老毛子固件】全自动脚本
* start.sh：立刻更新规则的脚本
* setting.sh：初次运行的脚本，自动修改配置与启用dnsmasq，只需要运行一次。
* del.sh：删除所有更改，出问题了只需要运行一下即可还原
* ▲以上脚本只适用于老毛子华硕固件，其他固件请勿直接使用
* H大的老毛子华硕固件：http://www.right.com.cn/forum/thread-161324-1-1.html ###
* 脚本参考自恩山论坛原帖：http://www.right.com.cn/forum/thread-184121-1-1.html ###
* 其他路由器固件需要自动脚本的朋友，请提供DNS配置文件［dnsmasq.conf］、定时任务［crontab］文件的路径给我才能制作脚本。

### 使用脚本
请先找个可以运行命令的终端控制区。如老毛子固件打开【网页终端】功能来运行命令或脚本。在【配置扩展环境】→启用【网页终端】→【打开网页终端】，进入终端界面后输入路由账号、密码即可开始。直接复制以下的一键命令执行即可。
* 一键运行命令（初次运行）：mkdir -p /etc/storage/dnsmasq/dns;cd /etc/storage/dnsmasq/dns;wget --no-check-certificate https://raw.githubusercontent.com/sy618/hosts/master/dnsmasq/setting.sh -O setting.sh;/bin/sh /etc/storage/dnsmasq/dns/setting.sh
* 一键还原命令（删除修改）：mkdir -p /etc/storage/dnsmasq/dns;cd /etc/storage/dnsmasq/dns;wget --no-check-certificate https://raw.githubusercontent.com/sy618/hosts/master/dnsmasq/del.sh -O del.sh;/bin/sh /etc/storage/dnsmasq/dns/del.sh

### 其他命令
* 查看规则文件dnsfq是否下载成功，命令cat /etc/storage/dnsmasq/dns/conf/dnsfq，即可看到第一行的update日期时间。
* 运行start脚本命令：/bin/sh /etc/storage/dnsmasq/dns/start.sh
* 更新start脚本文件：cd /etc/storage/dnsmasq/dns;wget --no-check-certificate https://raw.githubusercontent.com/sy618/hosts/master/dnsmasq/start.sh -O start.sh
* 下载start.sh脚本并运行：mkdir -p /etc/storage/dnsmasq/dns;cd /etc/storage/dnsmasq/dns;wget --no-check-certificate https://raw.githubusercontent.com/sy618/hosts/master/dnsmasq/start.sh -O start.sh;/bin/sh /etc/storage/dnsmasq/dns/start.sh
* 还原修改：/bin/sh /etc/storage/dnsmasq/dns/del.sh

