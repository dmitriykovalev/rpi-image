# rpi-image

## search

This command uses the same
[image list](https://downloads.raspberrypi.org/os_list_imagingutility_v3.json) as
[Raspberry Pi Imager](https://github.com/raspberrypi/rpi-imager).

Latest [Raspberry Pi OS](https://www.raspberrypi.com/software/operating-systems/)
images:
```bash
./rpi-image search
```

Latest images from all vendors (takes some time):
```bash
./rpi-image search --recursive
```

Filter by image filename using `--suffix` option:
```bash
./rpi-image search --suffix buster-armhf-lite
```

Print detailed information using `--json` or `-J` option:
```bash
./rpi-image search --suffix buster-armhf-lite --json
```
and use Python interpreter to pretty print:
```bash
./rpi-image search --suffix buster-armhf-lite --json | python3 -m json.tool
```

## download

Download image file and verify its checksum:
```bash
./rpi-image download --suffix buster-armhf-lite
```

## list

List image partitions:
```bash
sudo ./rpi-image list -i test.img
```

## expand

Expand last partition size by `128M`:
```bash
sudo ./rpi-image expand -i test.img -s +128M
```

Set last partition size to `2G` (must be bigger than the current size):
```bash
sudo ./rpi-image expand -i test.img -s 2G
```

## append

Append new `128M` partition:
```bash
sudo ./rpi-image append -i test.img -s 128M
```

Append new `1G` partition, setup `ext4` filesystem, use `data` as volume label:
```bash
sudo ./rpi-image append -i test.img -s 1G -fs ext4 -l data
```

## delete

Delete last partition:
```bash
sudo ./rpi-image delete -i test.img
```

## run

Run interactive shell inside the image:
```bash
sudo ./rpi-image run -i test.img
```

Run interactive shell as logged in `pi` user inside the image:
```bash
sudo ./rpi-image run -i test.img -u pi
```

Run `/bin/ls` inside the image:

```bash
sudo ./rpi-image run -i test.img /bin/ls
```

Run command inside the image as logged in `pi` user:
```bash
sudo ./rpi-image run -i test.img -u pi pwd
```
or
```bash
sudo ./rpi-image run -i test.img -u pi -- ls -la
```

Run shell script inside the image:
```bash
cat script.sh | sudo ./rpi-image run -i test.img -- /bin/bash
```

Run shell script with arguments inside the image:
```bash
cat script.sh | sudo ./rpi-image run -i test.img -- /bin/bash -s - arg1 arg2
```

Run shell script with arguments inside the image by mounting shell script file:
```bash
sudo ./rpi-image run -i test.img --bind-ro script.sh:/script.sh -- /script.sh arg1 arg2
```

Enable ssh:
```bash
sudo ./rpi-image run -i test.img touch /boot/ssh
```

Print OS info:
```bash
sudo ./rpi-image run --read-only -i test.img cat /etc/os-release
```
