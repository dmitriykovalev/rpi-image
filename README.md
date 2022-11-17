# rpi-image

## list

List available Raspbian OS images:
```
$ ./rpi-image list
```

## info

Show parition info:
```
$ ./rpi-image -i test.img info
```

## expand

Expand last partition by 128M:
```
$ sudo ./rpi-image -i test.img expand -s +128M
```

Set last parittion to 2G (must be bigger than current size):
```
sudo ./rpi-image -i test.img exapnd -s 2G
```

## run

Run `/bin/ls` inside image:

```
sudo ./rpi-image -i test.img run /bin/ls
```

Run command inside the image as logged in `pi` user:
```
$ sudo ./rpi-image -i test.img run -u pi pwd
$ sudo ./rpi-image -i test.img run -u pi -- ls -la
```

Enable ssh:
```
$ sudo ./rpi-image run -i test.img touch /boot/ssh
```

Print OS info:
```
$ sudo ./rpi-image run -ro -i test.img cat /etc/os-release
```
