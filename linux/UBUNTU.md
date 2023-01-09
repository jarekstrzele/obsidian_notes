#pop_shell
https://support.system76.com/articles/pop-shell/



#port 

aby sprawdzić, jaki program nasłuchuje na danym porcie 
`sudo lsof -i :8000`
`sudo lsof -i numer portu`



#ubuntu #linux #opera
###### problem z odtwarzaniem filmów w operze
#opera
https://gist.github.com/Thomas-Ln/c4ae803e90f9984b6612c8983c8fde1f
chodzi o plik `libffmpeg.so`
`cp libffmpeg.so /usr/lib/x86_64-linux-gnu/opera`


---
#bluetooth 
BLUeTOOTH:
wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-105b-e065.hcd
sudo cp BCM43142A0-105b-e065.hcd /lib/firmware/brcm/BCM.hcd


---
MEGA
https://flathub.org/apps/details/nz.mega.MEGAsync

---
MONGODB
#mongo_problems

gdy na ubuntu 22.04 nie moge zainstalować mongo:
```shell
echo "deb http://security.ubuntu.com/ubuntu impish-security main" | sudo tee /etc/apt/sources.list.d/impish-security.list

sudo apt-get update
sudo apt-get install libssl1.1

```

