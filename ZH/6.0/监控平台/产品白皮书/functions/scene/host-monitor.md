# 主机监控

主机监控是专门为查看主机和进程相关信息订制的一个场景，这个场景里面可以快速的获取到主机相关的信息。

## 前置步骤

当该业务下的 CMDB 没有主机的时候，主机监控的数据是空的。 所以先要学会如何在 CMDB 里面添加主机和增加进程信息，服务实例信息等。

* [如何创建业务并导入主机到业务中](../../../../配置平台/产品白皮书/快速入门/case1.md)
* [CMDB 主机进程管理](../../../../配置平台/产品白皮书/场景案例/CMDB_management_process.md)

**工作原理**：

操作系统的指标采集流程

![-w2020](media/16046499751434.jpg)

进程信息采集流程

![-w2020](media/16046499586323.jpg)

系统事件采集流程

![-w2020](media/16046500239629.jpg)

> 信息：系统事件，指监控默认采集的操作系统事件。

**主配置流程**：

* (1) 配置平台增加机器，配置业务拓扑和进程信息
* (2) 下发采集配置(自动)
* (3) 主机监控页面查看是否有数据上报

## 主功能一览

* 主机信息概览
* 主机视角(操作系统指标)
* 进程视角(进程指标)
* 产生系统事件

## 功能说明

### 主机列表页

![-w2020](media/15754451280250.jpg)

* 【1】**基本的汇总信息**：告警未恢复的主机数量，CPU 使用率超 80%的数量，应用内存使用率超 80%的主机数量，磁盘 IO 超 80%的主机数量
* 【2】
    * **采集下发**：对于 Agent 未安装的需要从节点管理或 CMDB 先安装 Agent，如果『无数据上报』情况可以使用采集下发按钮来触发采集器的下发和安装。
    * **指标对比**：选择不同的主机快速对比相同的指标。
    * **复制 IP**：可以批量复制 IP，复制的 IP 也可以在搜索条件里面使用格式是保持一致的。
* 【3】搜索条件和字段选择： 有多种搜索条件可以使用。

> 注意：想要通过业务拓扑来查主机么？在搜索里面选择集群模块可以达到按业务拓扑查询的效果。

* 【4】**置顶功能**：可以将自己关注主机进行置顶，后面的排序也是在置顶内的排序。
* 【5】**采集状态**：有如下几种状态：
    * 正常 ：数据采集正常
    * Agent 未安装： Agent 都没有就更不会有数据了，可以在 CMDB 和节点管理上安装好 Agent 监控的采集功能才可以使用。
    * 未知：判断不了的状态，就要联系管理员了。较少看到
    * 无数据上报：代表 Agent 安装了，可能 basereport 未安装或者异常，可以尝试再『采集下发』来重新安装主机-操作系统的默认采集器安装。
* 【6】**未恢复告警**：未恢复告警是当前事件中心中未恢复的相关主机的告警事件。
* 【7】**应用内存使用率**：除了内存使用率，还有其他的字段可以选择

![-w2020](media/15761393519097.jpg)

* 【8】**进程信息**：在 CMDB 里面配置的进程名称及简单的一个状态，红色代表的是有异常，点击进入可以查看。

#### 场景一： 查看某个集群下的机器磁盘空间使用情况进行排序 

![-w2021](media/15840812567108.jpg)

#### 场景二： 主机的监控指标对比

![-w2021](media/15840917617027.jpg)

### 主机详情页

![大图-数据对比-搜索-排序-分组](media/%E5%A4%A7%E5%9B%BE-%E6%95%B0%E6%8D%AE%E5%AF%B9%E6%AF%94-%E6%90%9C%E7%B4%A2-%E6%8E%92%E5%BA%8F-%E5%88%86%E7%BB%84.gif)

* 【1】**主机视角**：主要是查看主机-操作系统层面的指标。如 CPU MEM DISK 等。 详情查看 [主机-操作系统-指标](../addenda/host-metrics.md)
* 【2】**进程视角**：主要是查看进程层面的指标。详情查看[主机-进程-指标](../addenda/process-metrics.md)
* 【3】**视图控制**：主机场景的视图都相对比较简单，主要是满足开箱即用的需求，如果要做复杂的图表可以直接收藏到仪表盘中。
* 【4】**关联信息**：主机相关的信息，关联的告警事件和策略信息。
* 【5】**进程监控配置指标**：因为进程监控依赖 CMDB 的进程配置信息，所以需要熟悉 [CMDB 如何管理进程](../../../../配置平台/产品白皮书/场景案例/CMDB_management_process.md)

### 高级

basereport 采集器除了操作系统的指标和进程的指标采集，还会上报系统事件，当前内置 7 种系统事件 [主机-操作系统-系统事件](../addenda/host-events.md)

![-w2020](media/15766764588564.jpg)


