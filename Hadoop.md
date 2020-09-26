## Hadoop

- Hadoop 集群搭建：

**初次集群的时候格式化，后面不格式化**

- Hadoop历史：

  Nutch ---- 存储大量的网页数据（HDFS），计算（MapReduce）---Hadoop 1.x

  MapReduce --- 计算, YARN---集群，HDFS -- 存储 --- 2.x

  Hive -- SQL

- 三个模块：分布式，主从架构
  - HDFS：
    - Namenode：主节点，管理集群和保存元数据（元数据：描述性的数据）
    - Secondary NameNode：辅助Namenode做元数据管理
    - Datanote：从节点存储数据
  - yarn:
    - ResourceManager: 主节点，资源分配
    - NodeManager：从节点

- 工作方式：
  - 从节点datanode每三秒发送心跳到namenode

- 块和元数据大小：
  - 块所存数据的大小 --- 128M
  - hdfs block --- 150字节的元数据

进度：1.09 ---- 9.25
