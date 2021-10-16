# cloudflare-api-ddns 
  
说明：该脚本可实现自动更新cloudflare的dns记录，检查频率高达每分钟检查一次 
# 特点： 
     1、公网ip获取方式为从本机执行脚本获取，也就是执行命令的主机是自己拨号并有一个公网ip 
     2、需要用到ifconfig命令，需要安装net-tools这个软件包  
     3、因为用到了source命令，所以需要用bash执行环境，而不是sh  
     
备注： 关于第一点限制说明，执行脚本的主机必须有公网ip，这样就可以不受第三方接口的限制，比如接口频率限制，响应时间不稳定等，直接本机获取公网ip  

# 用法：
     1.安装 net-tools 选择自己适合的系统安装
      Ubuntu：apt-get install net-tools   CentOS：yum install net-tools
     2.上传文件到：/usr/local/bin/cf-ddns.sh  
     3.给权限：chmod +x /usr/local/bin/cf-ddns.sh  
     4.修改配置文件 #号里面
     5.测试 

##################################################################################################################################
# 申请Cloudflare Global API Key  申请地址https://dash.cloudflare.com/profile/api-tokens
CFKEY=1b7f1601e22b7cbd39252333f4afe3e5c0050

# Cloudflare 用户账号 邮箱		  											
CFUSER=1051239893@qq.com		   												

# 域名, eg: example.com	
CFZONE_NAME=jjzz.org

# 二级域名, eg: homeserver.example.com
CFRECORD_NAME=dip.jjzz.org

修改网卡地址：

执行命令 ifconfig 找到自己的IP网卡跟换：

比如我的是：我的IP网卡是eth0

[root@localhost ~]# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.199  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::fd99:a04:a9a2:4401  prefixlen 64  scopeid 0x20<link>
        inet6 fd3d:4853:8fb1::3b5  prefixlen 128  scopeid 0x0<global>
        inet6 fd3d:4853:8fb1:0:c87e:d4eb:627a:bf0c  prefixlen 64  scopeid 0x0<global>
        ether 52:54:00:3e:41:25  txqueuelen 1000  (Ethernet)
        RX packets 64504  bytes 21032593 (20.0 MiB)
        RX errors 0  dropped 1133  overruns 0  frame 0
        TX packets 72304  bytes 10454642 (9.9 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 68  bytes 5912 (5.7 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 68  bytes 5912 (5.7 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

修改PPP改成eth 
修改前：第95行：WAN_IP=`/usr/sbin/ifconfig |sed -n '/^ppp.*/{s/^\([^ ]*\) .*/\1/g;h;: top;n;/^$/b;s/^ \{1,\}inet \(.*\)  netmask.*/\1/g;p}'`
  
修改后：第95行：WAN_IP=`/usr/sbin/ifconfig |sed -n '/^eth.*/{s/^\([^ ]*\) .*/\1/g;h;: top;n;/^$/b;s/^ \{1,\}inet \(.*\)  netmask.*/\1/g;p}'`

##################################################################################################################################

 
B站视频介绍 https://www.bilibili.com/video/BV1A5411A7DR/  
油管视频介绍 https://www.youtube.com/watch?v=3XmMTWJI8XE   
