---
published: true
title: ZFS (Ubuntu)
tags: zfs linux system
---
## [ZFS -- baked directly into Ubuntu -- supported by Canonical.](http://blog.dustinkirkland.com/2016/02/zfs-is-fs-for-containers-in-ubuntu-1604.html)
- What does "support" mean?
	- You'll find zfs.ko automatically built and installed on your Ubuntu systems.  No more DKMS-built modules!
    - You'll see the module loaded automatically if you use it.
    - The user space zfsutils-linux package will be included in Ubuntu Main, with security updates provided by Canonical.
    
## Ref
- [ubuntu](https://wiki.ubuntu.com/Kernel/Reference/ZFS)
- [ZFS Concepts and Tutorial](https://linuxhint.com/zfs-concepts-and-tutorial/)
	- [Configuring ZFS Cache for High Speed IO](https://linuxhint.com/configuring-zfs-cache/)

# Maintenance
## [Check Data Integrity (scrub)](https://prefetch.net/blog/index.php/2011/10/15/using-the-zfs-scrub-feature-to-verify-the-integrity-of-your-storage/)
{% highlight bash %}
zpool scrub <rpool>			# start
zpool scrub -s <rpool> 		# stop

sudo zpool status	
cd /storage_pool
df -h .
{% endhighlight %}

## [Replacing a (silently) failing disk in a ZFS pool](https://imil.net/blog/2019/07/02/Replacing-a-silently-failing-disk-in-a-ZFS-pool/)

# Configuration
## [Pool - RAID5 / Z1](https://www.maketecheasier.com/use-zfs-filesystem-ubuntu-linux/)
    
{% highlight bash %}
sudo zpool create storage_pool raidz1 /dev/sda /dev/sdb /dev/sdc
sudo zpool status
cd /storage_pool
df -h .
{% endhighlight %}

## [Create ZFS dataset/Filesystem](https://www.jamescoyle.net/how-to/478-create-a-zfs-volume-on-ubuntu)

> At this point, we now have a zpool spanning three disks. One of these is used for parity, giving us the chance to recover in the event of a single disk failure. The next step is to make the volume usable and add features such as compression, encryption or de-duplication.

Multiple [Dataset](https://www.unixarena.com/2013/07/zfs-datasets-administration-and.html/) can be created on a single pool, the storage of the zpool with be available to any dataset as it requires it.

{% highlight bash %}
zfs create -o mountpoint=[MOUNT POINT] [ZPOOL NAME]/[DATASET NAME]

zfs create -o mountpoint=/mnt/binaries storage_pool/binaries
zfs list   # Test the datasets have been created with
{% endhighlight %}
  
## [ZFS Event Daemon (ZED)](https://zfsonlinux.org/manpages/0.8.4/man8/zed.8.html)
  
> What ZED does that is so great is that it provides a very simple way to take action when ZFS events happen. - [In praise of ZFS On Linux's ZED](https://utcc.utoronto.ca/~cks/space/blog/linux/ZFSZEDPraise)

 
## [ZFS RAIDZ expansion](https://www.reddit.com/r/homelab/comments/83wo88/any_news_on_zfs_raidz_expansion/)
### [Expanding a RAIDZ Pool](https://serverfault.com/questions/537047/expanding-a-freenas-raidz-pool)
  
> With ZFS, you either have to buy all storage you expect to need upfront, or you will be wasting a few hard drives on redundancy you don't need. - [You can't add hard drives to a VDEV](https://louwrentius.com/the-hidden-cost-of-using-zfs-for-your-home-nas.html)
  
- [github WP](https://github.com/openzfs/zfs/pull/8853)
When available **ZFS RAIDZ expansion** would let adding a new disk to existing vdev with rebalancing. [video](https://www.youtube.com/watch?v=ZF8V7Tc9G28)

The main takeaway of this picture is that your ZFS pool and thus your file system is based on one or more VDEVs. And those VDEVs contain the actual hard drives.

Fault-tolerance or redundancy is addressed within a VDEV. A VDEV is either a RAID-1 (mirror), RAID-5 (RAIDZ) or RAID-6 (RAIDZ2).

![caption](https://louwrentius.com/static/images/zfs-overview.png)
