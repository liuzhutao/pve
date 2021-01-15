# PVE6.3 安装配置部署与虚拟机配置

https://blog.csdn.net/allway2/article/details/102946660?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522160977128916780255282501%252522

安装步骤参考以上连接

## PVE的安装与集群搭建

1. 启动机房102服务器，进入此界面时按F12

![IMG_20210113_200551](C:\Users\64858\Documents\Tencent Files\154902823\FileRecv\MobileFile\IMG_20210113_200551.jpg)

2. 选择插入的USB系统盘安装方式

![IMG_20210113_200648](C:\Users\64858\Documents\Tencent Files\154902823\FileRecv\MobileFile\IMG_20210113_200648.jpg)

3. 默认选择，点enter进入

![IMG_20210113_200657](C:\Users\64858\Documents\Tencent Files\154902823\FileRecv\MobileFile\IMG_20210113_200657.jpg)

4. 按如下图片配置![IMG_20210113_200744](C:\Users\64858\Documents\Tencent Files\154902823\FileRecv\MobileFile\IMG_20210113_200744.jpg)

   

   ![](C:\Users\64858\Documents\Tencent Files\154902823\FileRecv\MobileFile\IMG_20210113_200758.jpg)

【时区设置为china】	![IMG_20210113_200812](C:\Users\64858\Documents\Tencent Files\154902823\FileRecv\MobileFile\IMG_20210113_200812.jpg)

【设置密码】【邮箱随便写只要有效就好】

![image-20210113211250604](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210113211250604.png)



![image-20210113211333730](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210113211333730.png)

点击Install,等待安装即可

![image-20210113211409898](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210113211409898.png)



5. 安装结束后，连接实验室VPN，浏览器地址栏输入：https://192.168.1.102:8006

【用户名是root】

【密码是自己设置的】

![](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210113211736669.png)

6. 创建集群

【依次按照图片点击，填写名称】

![image-20210113212312845](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210113212312845.png)



7. 通过Xshell连接其他的物理机（103，104）

【登录用户名：root】

【密码：自己设置的】

输入以下命令加入集群：

```
pvecm add 192.168.1.102
```

然后输入102的密码，默认yes 完成后面的配置

![image-20210113212809345](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210113212809345.png)

然后就可以看到web网页显示是OK的了

![image-20210113213130303](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210113213130303.png)





## 为什么放弃了Ceph

pve集成了ceph,但是奈何实验室物理机配置跟不上，对网络的要求比较高，故放弃。

![image-20210114230928055](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210114230928055.png)

NFS配置的文章

https://blog.csdn.net/li4528503/article/details/106344653/



## 在PVE上安装虚拟机

1. 首先上传虚拟机镜像

![image-20210114231330953](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210114231330953.png)



2. 单击物理节点，右键创建虚拟机

![image-20210114231428041](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210114231428041.png)





3. 配置虚拟机

<span style='color:red;background:背景颜色;font-size:25px;font-family:字体;'>**虚拟机可以在创建的时候命名，命名方式建议为“名称+ip”：比如我想创建一个名为master的虚拟机，ip地址为192.168.1.30，则命名为master30**</span>



![image-20210115150103507](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115150103507.png)



![image-20210115150602797](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115150602797.png)



![image-20210115150630726](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115150630726.png)

<span style='color:red;background:背景颜色;font-size:25px;font-family:字体;'>**【存储放在nfs盘上可以以后虚拟机迁移】**</span>

![image-20210115150735928](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115150735928.png)



![image-20210115150813029](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115150813029.png)



![image-20210115150825233](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115150825233.png)





![image-20210115150848302](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115150848302.png)



![image-20210115150921489](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115150921489.png)



## 为虚拟机安装Ubuntu系统+网络配置

1. 右键新创建的虚拟机然后启动

![image-20210115151228184](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115151228184.png)





2 Ubuntu的默认安装模式就可（一直enter）记得要勾选ssh就好

![image-20210115151950395](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115151950395.png)



3. 输入用户密码登录

![image-20210115152714186](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115152714186.png)



4. 进入root模式，修改文件网络配置文件，让虚拟机能够Ping通外网

<span style='color:red;background:背景颜色;font-size:25px;font-family:字体;'>**关于虚拟机创建时，注意创建的ip地址范围是192.168.1.30-192.168.1.99**</span>


```
sudo -i
```

```
vim /etc/netplan/00-installer-config.yaml
```

```
network:
  ethernets:
    ens18:
      addresses: [192.168.1.30/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [192.168.1.1]
      dhcp4: false
      optional: true
```

```
netplan apply
```

## 虚拟机备份

![image-20210115171549501](C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115171549501.png)



备份完成

<img src="C:\Users\64858\AppData\Roaming\Typora\typora-user-images\image-20210115164146615.png" alt="image-20210115164146615" style="zoom:50%;" />





## 常见问题

1. 如果proxmax结点可以通过xshell连接但是不能在web页面打开，那就使用以下命令重启代理服务

```
systemctl restart pveproxy pvedaemon
```

## 使用注意事项

1. 关于虚拟机创建时，注意创建的ip地址范围是`192.168.1.30-192.168.1.99`.
2. 如果以后需要迁移，那就把虚拟机创建在nfs盘（nfsproxmox）上
3. 虚拟机可以在创建的时候命名，命名方式建议为“名称+ip”：比如我想创建一个名为master的虚拟机，ip地址为192.168.1.30，则命名为master30

4. 创建好的虚拟机用Xshell连接使用