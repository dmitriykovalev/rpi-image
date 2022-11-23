# rpi-image

## urls

List available [Raspberry Pi OS](https://www.raspberrypi.com/software/operating-systems/) image file URLs:
```
./rpi-image urls
```

## list

List image partitions:
```
sudo ./rpi-image list -i test.img
```

## expand

Expand last partition size by `128M`:
```
sudo ./rpi-image expand -i test.img -s +128M
```

Set last partition size to `2G` (must be bigger than the current size):
```
sudo ./rpi-image expand -i test.img -s 2G
```

## append

Append new `128M` partition:
```
sudo ./rpi-image append -i test.img -s 128M
```

Append new `1G` partition, setup `ext4` filesystem, use `data` as volume label:
```
sudo ./rpi-image append -i test.img -s 1G -fs ext4 -l data
```

## delete

Delete last partition:
```
sudo ./rpi-image delete -i test.img
```

## run

Run interactive shell inside the image:
```
sudo ./rpi-image run -i test.img
```

Run interactive shell as logged in `pi` user inside the image:
```
sudo ./rpi-image run -i test.img -u pi
```

Run `/bin/ls` inside the image:

```
sudo ./rpi-image run -i test.img /bin/ls
```

Run command inside the image as logged in `pi` user:
```
sudo ./rpi-image run -i test.img -u pi pwd
sudo ./rpi-image run -i test.img -u pi -- ls -la
```

Run shell script inside the image:
```
cat script.sh | sudo ./rpi-image run -i test.img -- /bin/bash
```

Run shell script with arguments inside the image:
```
cat script.sh | sudo ./rpi-image run -i test.img -- /bin/bash -s - arg1 arg2
```

Run shell script with arguments inside the image by mounting shell script file:
```
sudo ./rpi-image run -i test.img --bind-ro script.sh:/script.sh -- /script.sh arg1 arg2 arg3
```

Enable ssh:
```
sudo ./rpi-image run -i test.img touch /boot/ssh
```

Print OS info:
```
sudo ./rpi-image run --read-only -i test.img cat /etc/os-release
```
