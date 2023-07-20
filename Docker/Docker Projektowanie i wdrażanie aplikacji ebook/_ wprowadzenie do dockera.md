[[_start Docker Projektowanie i wdrażanie aplikacji]]

- 2013 Docker udostępniony jak *open source*
- 

> ==podstawowa idea==
> umieścić aplikację z jej wszystkimi zależnościami w jednostce standaryzowanej pod kątem procesu tworzenia i wdrażania oprogramowania

**Kontener dockera zawiera**:
- kod programu
- narzędzia i biblioteki systemowe,
- środowisko uruchomieniowe wraz z gotową konfiguracją

Obrazy Dockera funkcjonuja w obrębie jądra tego samego systemu operacyjnego
Kontener ma własnyy system plików i zmienne środowiskowe

**Korzyści**
- szybkość i wielkość (docker współużytkuje wyłącznie jądro)
- odtwarzalne i przenośne kompilacje
- trwała i "zwinna" infrastruktura (Dockerfile)

## NARZĘDZIA
### DOCKER Engine
==Docker to aplikacja *klient-serwer*==
Docker udostępnia interfejs *API REST*, który okręsla interfejsy prowadzące interakcję z demonem.

==Klient DOckera== to program wiersza poleceń służący do zarządzania hostami Docker a uruchomionymi kontenerami sys Linux. Komendy lienta są zamieniana na odpowiednie zapytanie interfesu *REST API*, a następnie wysyłane do serwera Dockera

### Compose Docker
==Compose== to narzędzie wykonywane z posiomu wiersza poleceń jako polecenie `docker-compose`.
Służy do definiowania i uruchamiania aplikacji docker z wieloma kontenerami






















