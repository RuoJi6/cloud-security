docker渗透基础知识

在后面文章中，可以使用kali当作靶场
```shell
 sudo apt update
 sudo apt install docker.io 
```


在docker中得逃逸有：

1、管理员配置不当产生得逃逸

2、docker版本逃逸

3、宿主机系统本身存在漏洞

在逃逸中需要：
1、docerk shell用户是高权限用户：root等，因为有些操作需要高权限进行触发

<b>:closed_lock_with_key:权限的划分</b>
| UID    | 数值                                                        | 比如：       |
| ------ | ----------------------------------------------------------- | ------------ |
| 0      | 超级管理员（root用户）                                      | root         |
| 1～999 | Linux系统将一些服务程序和系统任务分配给独立的系统用户来运行 | bin          |
| 1000   | 普通用户UID从1000开始                                       | www-data,www |
