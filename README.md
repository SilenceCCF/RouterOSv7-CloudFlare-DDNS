# RouterOSv7-CloudFlare-DDNS
支持 CloudFlare 域名动态解析的 RouterOS V7 脚本

特点：
1. 支持多路 PPPOE 拨号。
2. 不生成临时文件，不定义临时的全局变量。
3. 支持发送钉钉消息（如不需要把 dingtalk 值留空或相关语句屏蔽即可）。

说明：
1. PPP_Profile_OnUp.txt 脚本的内容放在 /ppp/Profiles 处，打开 pppoe 拨号使用的那个 profile 条目，填写在 scripts 标签页下的 On Up 编辑框里。
2. 如不需要发送钉钉消息，将相关内容屏蔽即可，也可参考代码自行改成其它 WebHook。
3. CloudFlare_DDNS.txt 脚本在 /system/scripts 处添加。
4. CloudFlare 的 Token 和 ZoneId 数据需要自行在 CloudFlare 官网上去设置或查找。

和其它常用类似功能的脚本需要手工指定拨号接口、需要从 /ip/address 处查询 IP、甚至需要生成全局变量或临时文件不同，这个脚本的有趣之处在利用 On Up 事件时系统返回的端口 ID 号和 IP 地址，并巧妙地传递给了修改域名解析的脚本（RouterOS 脚本并不支持命令行方式传入参数）。
