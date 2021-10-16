# cloudflare-api-ddns 
  
说明：该脚本可实现自动更新cloudflare的dns记录，检查频率高达每分钟检查一次 
# 特点： 
     1、公网ip获取方式为从本机执行脚本获取，也就是执行命令的主机是自己拨号并有一个公网ip 
     2、需要用到ifconfig命令，需要安装net-tools这个软件包  
     3、因为用到了source命令，所以需要用bash执行环境，而不是sh  
     
备注： 关于第一点限制说明，执行脚本的主机必须有公网ip，这样就可以不受第三方接口的限制，比如接口频率限制，响应时间不稳定等，直接本机获取公网ip  

# 用法
     1.上传文件到：/usr/local/bin/cf-ddns.sh  
     2.给权限：chmod +x /usr/local/bin/cf-ddns.sh  
     3.修改配置文件：


# 申请Cloudflare Global API Key  申请地址https://dash.cloudflare.com/profile/api-tokens
CFKEY=1b7f1601e22b7cbd39252333f4afe3e5c0050

# Cloudflare 用户账号 邮箱		  											
CFUSER=1051239893@qq.com		   												

# 域名, eg: example.com	
CFZONE_NAME=jjzz.org

# 二级域名, eg: homeserver.example.com
CFRECORD_NAME=dip.jjzz.org

##################################################################################################################################

 
B站视频介绍 https://www.bilibili.com/video/BV1A5411A7DR/  
油管视频介绍 https://www.youtube.com/watch?v=3XmMTWJI8XE   
