# Kernels and modules with RT (RealTime) patch:

- linux-rt-bfq

- linux-rt-bfq-git

###### linux-rt-bfq/linux-rt-bfq-git incorporates:

* [bfq improvements](https://groups.google.com/forum/#!forum/bfq-iosched) - latest fixes authored by Paolo Valente and BFQ Team

* [bfq-dev](https://github.com/Algodev-github/bfq-mq/commits/dev-bfq-on-5.2) - latest fixes authored by Paolo Valente and BFQ Team

* [LL-patches](https://github.com/sirlucjan/kernel-patches/tree/master/5.1/ll-patches) / [LL-patches](https://gitlab.com/sirlucjan/kernel-patches/tree/master/5.1/ll-patches) - specific patches authored by Piotr Gorski

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

# Enable bfq-mq

For now, you can use `sudo tee /sys/block/sda/queue/scheduler <<< bfq-mq` to enable "bfq-mq".

You can also add this to file `60-schedulers.rules`:

```
# Non-rotational disks
ACTION=="add|change", KERNEL=="sd[a-z]", ATTR{queue/rotational}=="0", ATTR{queue/scheduler}="bfq-mq"
# Rotational disks
ACTION=="add|change", KERNEL=="sd[a-z]", ATTR{queue/rotational}=="1", ATTR{queue/scheduler}="bfq-mq"
```

and run a command `sudo udevadm control --reload && sudo udevadm trigger`
