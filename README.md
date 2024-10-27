
我的电脑最近经常抽疯，时不时卡顿一次


检查系统事件日志，会有这俩个：


1. 发出了对设备 \\Device\\RaidPort0 的重置。
2. 已在磁盘 0 (PDO 名称: \\Device\\0000003a)的逻辑块地址 0x7206a8 处重试 IO 操作。


![](https://img2024.cnblogs.com/blog/685541/202410/685541-20241024232740751-230398435.png)


DiskGenis检查磁盘0，是正常的：


![](https://img2024.cnblogs.com/blog/685541/202410/685541-20241024232802713-1779929928.png)


这个FASPEED硬盘是国产士必得牌子的。京东商城找到FASPEED，没找到官方旗舰店，只有一个类似代理的店铺，问客服硬盘问题1天也没回复。


下载HD Tune工具，检测磁盘Health，看到有一个CRC错误数量，不确定卡顿是否和这个有关：


![](https://img2024.cnblogs.com/blog/685541/202410/685541-20241024232904673-1106947743.png)


看到CRC错误，网上搜索一下。参考[如何修复 HD Tune 中的“接口 CRC 错误计数”](https://github.com)这篇文章，貌似这个CRC错误可能与SATA控制器有关。


另外[WIN10卡顿，system进程硬盘占用100%，iaStorA警告事件，发出了对设备 \\Device\\RaidPort0 的重置。\_system占用磁盘100%\-CSDN博客](https://github.com)这篇博客也介绍了类似的问题，大概率不小心更新了SATA驱动版本导致的问题，通过更新查找本地SATA驱动回退版本解决。


但我本地是没有其它SATA驱动版本的，自动搜索最新驱动显示最新版本。当前我的版本是2006年的10\.0\.22000\.856微软官方版本，比较老了。


下载驱动精灵，看到SATA可以升级一个Intel的最新版本：


![](https://img2024.cnblogs.com/blog/685541/202410/685541-20241025001431794-1437337762.png)


于是我点击升级。重启多次，然后使用电脑超6个小时，未复现卡顿问题了，解决！


另外，我重新打开DiskGenis工具，看看磁盘情况，发现硬盘顺序变了。不确定这个硬盘顺序因驱动重装变化，是否也与卡顿问题解决有关系：


![](https://img2024.cnblogs.com/blog/685541/202410/685541-20241025002812286-694334598.png)


 


参考资料：


[解决windows 10 事件日志中出现 发出对设备\\Device\\RaidPort1的重置的13个解决办法 \- 使用经验 \- 我爱帮助网](https://github.com)


[SSD突然一直被占用读写卡顿，重启后发现大量事件ID为129、153的警告 \- Microsoft Community](https://github.com):[wgetCloud机场](https://tabijibiyori.org)


[WIN10卡顿，system进程硬盘占用100%，iaStorA警告事件，发出了对设备 \\Device\\RaidPort0 的重置。\_system占用磁盘100%\-CSDN博客](https://github.com)


[如何修复 HD Tune 中的“接口 CRC 错误计数”](https://github.com)


