## 环境配置：
 - IP （Under Virtualbox）

    - enps3: Nat Network--- dhcp or static --- access the network

    - enps8: host-only --- static ip --- access VMs

      ```
      vi /etc/sysconfig/network-scripts/ifcfg-enp0s # edit the network setting
      
      # static or dhcp
      # name
      
      IPADDR =
      NETWORK =
      GATEWAY = 
      DNS1 = 
      ```

      

-  Firewall  

  ```
  systemctl stop firewalld # stop the firewall service
  system status firewall # check the status
  systemctl disable firewalld # stop from the start
  ```

- Vim:

  ```
  yum -y install vim
  vim /etc/selinux/config
  # disabled --- SELINUX
  ```

- Change the hostname

  ```
  vim /etc/hostname
  # node01.kaikeba.com
  ```

- Change the map relationship

  ```
  vim /etc/hosts
  # 192.168.52.100 node01.kaikeba.com node01
  # 192.168.52.110 node02.kaikeba.com node02
  # 192.168.52.120 node03.kaikeba.com node03
  ```

- Time parallel

  ```
  yum -y insatll ntpdate
  crontab -e
  */1 * * * * /usr/sbin/ntpdate time1.aliyun.com
  ```

- Add user

```
useradd hadoop
passwd hadoop
visudo
/root
# hadoop ALL=(ALL) ALL
```

- create directory to save package

  ```
  mkdir -p /kkb/soft
  mkdir -p /kkb/soft
  chown -R hadoop:hadoop /kkb
  ```

- Install JDK

  ```
  
  ```

  