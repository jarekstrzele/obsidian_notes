[[_ Intro Docker Mumshad]]




---
# TAG  
```shell
$ docker run ubuntu cat /etc/*release*  

DISTRIB_ID=Ubuntu  
DISTRIB_RELEASE=20.04  
DISTRIB_CODENAME=focal  
DISTRIB_DESCRIPTION="Ubuntu 20.04.3 LTS"  
NAME="Ubuntu"  
VERSION="20.04.3 LTS (Focal Fossa)"  
ID=ubuntu  
ID_LIKE=debian  
PRETTY_NAME="Ubuntu 20.04.3 LTS"  
VERSION_ID="20.04"  
HOME_URL="[https://www.ubuntu.com/](https://www.ubuntu.com/ "https://www.ubuntu.com/")"  
SUPPORT_URL="[https://help.ubuntu.com/](https://help.ubuntu.com/ "https://help.ubuntu.com/")"  
BUG_REPORT_URL="[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/ "https://bugs.launchpad.net/ubuntu/")"  
PRIVACY_POLICY_URL="[https://www.ubuntu.com/legal/terms-and-policies/privacy-policy](https://www.ubuntu.com/legal/terms-and-policies/privacy-policy "https://www.ubuntu.com/legal/terms-and-policies/privacy-policy")"  
VERSION_CODENAME=focal  
UBUNTU_CODENAME=focal  
```
  

You want to use another version of Ubuntu  
```shell 
$ docker run ubuntu:17.10 cat /etc/*release*  

DISTRIB_ID=Ubuntu  
DISTRIB_RELEASE=17.10  
DISTRIB_CODENAME=artful  
DISTRIB_DESCRIPTION="Ubuntu 17.10"  
NAME="Ubuntu"  
VERSION="17.10 (Artful Aardvark)"  
ID=ubuntu  
ID_LIKE=debian  
PRETTY_NAME="Ubuntu 17.10"  
VERSION_ID="17.10"  
HOME_URL="[https://www.ubuntu.com/](https://www.ubuntu.com/ "https://www.ubuntu.com/")"  
SUPPORT_URL="[https://help.ubuntu.com/](https://help.ubuntu.com/ "https://help.ubuntu.com/")"  
BUG_REPORT_URL="[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/ "https://bugs.launchpad.net/ubuntu/")"  
PRIVACY_POLICY_URL="[https://www.ubuntu.com/legal/terms-and-policies/privacy-policy](https://www.ubuntu.com/legal/terms-and-policies/privacy-policy "https://www.ubuntu.com/legal/terms-and-policies/privacy-policy")"  
VERSION_CODENAME=artful  
UBUNTU_CODENAME=artful  
```




`docker attach conterner_id`
#docker/attach
zmienia mode z detached na attached   

  ---
  