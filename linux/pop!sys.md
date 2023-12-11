# duo boot
`sudo fdisk -l`
select `EFI System` (sda1)
```bash
$ sudo mkdir /mnt/windows
$ sudo mount /dev/sda1 /mnt/windows
$ sudo cp -r /mnt/windows/EFI/Microsoft /boot/efi/EFI
$ sudo ls /boot/efi/EFI 
# you have to see BOOT Linux Microsoft Po_OS....
```

`sudo nano /boot/efi/loader/loader/conf`
in /boot/efi/loader/loader.conf
```
default Pop_OS-current
timeout 5
console-mode max
```

restart

