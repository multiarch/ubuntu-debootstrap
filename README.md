# ubuntu-debootstrap

## Usage

Once you need to configure binfmt-support on your Docker host.
This works locally or remotely (i.e using boot2docker or swarm).

```console
# configure binfmt-support on the Docker host (works locally or remotely, i.e: using boot2docker)
$ docker run --rm --privileged multiarch/qemu-user-static:register --reset
```

Then you can run an `armhf` image from your `x86_64` Docker host.

```console
$ docker run -it --rm multiarch/ubuntu-debootstrap:armhf-wily
root@a0818570f614:/# uname -a
Linux a0818570f614 4.1.13-boot2docker #1 SMP Fri Nov 20 19:05:50 UTC 2015 armv7l armv7l armv7l GNU/Linux
root@a0818570f614:/# exit
```

Or an `x86_64` image from your `x86_64` Docker host, directly, without qemu emulation.

```console
$ docker run -it --rm multiarch/ubuntu-debootstrap:amd64-wily
root@27fe384370c9:/# uname -a
Linux 27fe384370c9 4.1.13-boot2docker #1 SMP Fri Nov 20 19:05:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
root@27fe384370c9:/#
```
