- ## 环境配置：

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
  
       
  
  - Firewall  
  
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
    mkdir -p /kkb/install
    chown -R hadoop:hadoop /kkb
    ```
  
  - Install JDK
  
    ```
    yum -y install lrzsz
    # pull the file to /soft folder
    tar -zxf xxx.tar.gz -C /kkb/install/
    cd xxx
    # change the priviledge
    sudo vim /etc/profile
    # add two lines:
    ​```
    export JAVA_HOME=/kkb/install/jdk1.8.0_141
    export PATH=:$JAVA_HOME/bin:$PATH
    ​```
    # activate the settings
    source /etc/profile
    # check the version of java
    java -version
    cd /kkb/install 
    scp -r jdk/ node02:$PWD (the current directory)
    scp -r jdk/ node03:$PWD
    ```
  
  - login without password
  
    ```
    # on node1
    ssh-keygen -t rsa
    # copy the public key to node1 (do it on all three hosts)
    ssh-copy-id node01
    
    # send the authorized_keys to other two machines
    cd ~
    cd .ssh
    scp authorized_keys node02:$PWD
    scp authorized_keys node03:$PWD
    # reboot all the sessions on centos/root 
    reboot -h now
    ```
  
- Download zookeeeper

  ```
  cd /kkb/soft
  tar -zxvf xxx -C /kkb/install
  cd /kkb/install/xxx/conf
  mv zoo_sample.cfg zoo.cfg
  cd /kkb/install/xxx
  mkdir -p zkdatas
  cd zkdatas
  
  ```

  