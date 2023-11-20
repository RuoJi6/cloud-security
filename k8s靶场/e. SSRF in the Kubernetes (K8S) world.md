SSRF in the Kubernetes (K8S) world

K8s中的ssrf

地址：http://192.168.86.139:1232/

此方案旨在展示在云环境中随处可见的流行应用程序安全漏洞。现在，我们将尝试看看它如何影响 Kubernetes 集群、内部服务和微服务。这在云原生环境中产生了相当大的影响，其中一个实际示例包括 [Shopify - Exchange 中的 SSRF 导致所有实例的 ROOT](https://hackerone.com/reports/341876) 访问。

在方案结束时，我们将了解和学习以下内容

1.  如何利用云环境中应用程序中的SSRF漏洞

2.  了解如何了解元数据查询功能，以获取对云提供商数据的访问权限

3.  了解并利用 Kubernetes 原生服务发现功能和服务 DNS 查询

4.  访问群集环境中的内部微服务

【这个页面访问需要很久，需要等待】

> **ssrf-元数据**: [地址](https://mp.weixin.qq.com/s/oMuoJD8O6bYWEuUFmY_iOA) {src挖掘之元数据}
>
>  
>
> 通过枚举端口
>
> GET <http://127.0.0.1:5000>
>
> ![image-20231120170227091](./assets/image-20231120170227091.png)
>
>  
>
> ![image-20231120170231879](./assets/image-20231120170231879.png)
>
>  
>
>  
>
> 但是不知道为什么我这里返回的是""
>
> ![image-20231120170235463](./assets/image-20231120170235463.png)
>
> 官方的演示是：
>
> ![image-20231120170239047](./assets/image-20231120170239047.png)
>
>  
>
> 这里可以查看我另外写的文章：[链接](https://mp.weixin.qq.com/s/oMuoJD8O6bYWEuUFmY_iOA)
>
> 如果有人复现出来请告诉我错误
