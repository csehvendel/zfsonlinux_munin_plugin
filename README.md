A port of ZFS stats for FreeBSD plugin to Linux
Author of the original plugin: David Bjornsson <dabb@lolnet.is>
Author of the Linux port: Alex Chistyakov <alexclear@gmail.com>
some tweaks by Vendel Cseh <csehvendel@gmail.com>
Usage: zfs_stats_FUNCTION

Available functions:
      efficiency - ARC efficiency
      cachehitlist - Cache hit by cache list
      cachehitdtype - Cache hit by data type
      utilization - ARC size breakdown
      l2utilization - L2ARC size breakdown
      l2efficiency - L2ARC efficiency



getting the variables is very very slow on original linux port..........

 time cat /proc/spl/kstat/zfs/arcstats | grep "^hits" | awk '{print $3;}'

 real  0m0.008s
 user  0m0.005s
 sys   0m0.011s


 time awk '/^hits/{print $3}' /proc/spl/kstat/zfs/arcstats

 real  0m0.003s
 user  0m0.001s
 sys   0m0.002s

