# rpi-image

## list

List available Raspbian OS images:
```
$ ./rpi-image list
```

## info

Show parition info:
```
$ ./rpi-image info -i test.img
```

## expand

Expand last partition by 128M:
```
$ sudo ./rpi-image expand -i test.img -s +128M
```

Set last parittion to 2G (must be bigger than current size):
```
sudo ./rpi-image expand -i test.img -s 2G
```

## run

Run `/bin/ls` inside image:

```
sudo ./rpi-image run -i test.img /bin/ls
```

Run command inside the image as logged in `pi` user:
```
$ sudo ./rpi-image run -i test.img -u pi pwd
$ sudo ./rpi-image run -i test.img -u pi -- ls -la
```

Enable ssh:
```
$ sudo ./rpi-image run -i test.img touch /boot/ssh
```

Print OS info:
```
$ sudo ./rpi-image run -ro -i test.img cat /etc/os-release
```

