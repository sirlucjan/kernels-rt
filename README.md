[![Packaging status](https://repology.org/badge/vertical-allrepos/linux-rt-bfq.svg)](https://repology.org/project/linux-rt-bfq/versions)

# Kernels and modules with RT (RealTime) patch:

- linux-rt-bfq

- linux-rt-bfq-git

###### linux-rt-bfq/linux-rt-bfq-git incorporates:

* [bfq improvements](https://groups.google.com/forum/#!forum/bfq-iosched) - latest fixes authored by Paolo Valente and BFQ Team

* [bfq-dev](https://github.com/Algodev-github/bfq-mq/commits/dev-bfq-on-5.2) - latest fixes authored by Paolo Valente and BFQ Team

* [LL-patches](https://github.com/sirlucjan/kernel-patches/tree/master/5.1/ll-patches) / [LL-patches](https://gitlab.com/sirlucjan/kernel-patches/tree/master/5.1/ll-patches) - specific patches authored by Piotr Gorski

* [bfq-lucjan-dev](https://github.com/sirlucjan/bfq-mq-lucjan/commits/dev-bfq-on-5.2-lucjan) - latest fixes authored by Paolo Valente and BFQ Team and forked by Piotr Gorski

***
# Download:

```
git clone https://github.com/sirlucjan/kernels-rt.git

```

or

```
git clone https://gitlab.com/sirlucjan/kernels-rt.git

```
# Install:


```
cd /some_path/kernels-rt/package_name
makepkg -srci

```

# Enable bfq

~~For now, you can use `sudo tee /sys/block/sda/queue/scheduler <<< bfq` to enable "bfq".~~

~~You can also add this to file `60-schedulers.rules`:~~

```
# Non-rotational disks
ACTION=="add|change", KERNEL=="sd[a-z]", ATTR{queue/rotational}=="0", ATTR{queue/scheduler}="bfq"
# Rotational disks
ACTION=="add|change", KERNEL=="sd[a-z]", ATTR{queue/rotational}=="1", ATTR{queue/scheduler}="bfq"
```

~~and run a command `sudo udevadm control --reload && sudo udevadm trigger`~~

For now, bfq is enabled by default! [(since 5.0-lucjan-ll1-rc1.patch and LL-elevator-set-default-scheduler-to-bfq-for-blk-mq.patch)](https://github.com/sirlucjan/kernel-patches/blob/master/5.0/ll-patches/0002-LL-elevator-set-default-scheduler-to-bfq-for-blk-mq.patch)
