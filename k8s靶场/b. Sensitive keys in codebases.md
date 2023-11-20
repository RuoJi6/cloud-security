**Sensitive keys in codebases**

代码库中敏感信息

<http://192.168.86.139:1230/>

使用目录扫描工具进行扫描

![image-20231120165349638](./assets/image-20231120165349638.png)

直接发现是.get文件泄漏

![image-20231120165353706](./assets/image-20231120165353706.png)

使用git扫描工具下载文件

在下载目录使用git查看提交的Log日志

![image-20231120165358193](./assets/image-20231120165358193.png)

 

发现

![image-20231120165402501](./assets/image-20231120165402501.png)

 

切换分支：git checkout d7c173ad183c574109cd5c4c648ffe551755b576

![image-20231120165407309](./assets/image-20231120165407309.png)

成功读取到

![image-20231120165410566](./assets/image-20231120165410566.png)

 
