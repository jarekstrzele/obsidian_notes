#avaloniaui 


>[!imporant] AvaloniaUI 
> to zestaw narzędzi do budowy interfejsu użytkownika, 
> inspirowany WPF, ale przeznaczony do pracy na wielu platformach, w tym na Linux, macOS i Windows. D



# 1. Zainstaluj .NET Core SDK

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-6.0

```


`apt-transport-https` umożliwia on APT korzystanie z HTTPS do komunikacji z serwerami repozytoriów.









