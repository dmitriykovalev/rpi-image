# rpi-image

## list

List available [Raspberry Pi OS](https://www.raspberrypi.com/software/operating-systems/) images:
```
./rpi-image list
```

## info

Show partition info:
```
./rpi-image info -i test.img
```

## expand

Expand last partition by `128M`:
```
sudo ./rpi-image expand -i test.img -s +128M1
```

Set last partition to `2G` (must be bigger than current size):
```
sudo ./rpi-image expand -i test.img -s 2G
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

Enable ssh:
```
sudo ./rpi-image run -i test.img touch /boot/ssh
```

Print OS info:
```
sudo ./rpi-image run --read-only -i test.img cat /etc/os-release
```
