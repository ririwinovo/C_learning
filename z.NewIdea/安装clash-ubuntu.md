# 1-获取ip
ubuntu指令：ip addr

# 2-订阅地址修改

>进入 /download/clash-for-linux-master文件夹
>sudo vim /etc/profile.d/clash.sh
>修改其中的内容为ip 如 /http://192.168.239.128/
>环境变量：source /etc/profile.d/clash.sh


# 3-浏览器访问

>sudo bash start.sh
>浏览器输入http://<\ip>:9090/ui 其中 ip 位置填入

# 4-指令

>请执行以下命令加载环境变量: source /etc/profile.d/clash.sh
>请执行以下命令开启系统代理: proxy_on
>若要临时关闭系统代理，请执行: proxy_off
