

# Docker. Kurs video. Praca z systemem konteneryzacji i Docker Swarm
[[3.1.  tryb interaktywny]]
[[3.2. Wolumeny]]
[[3.3. Sieci dockerowe]]
[[3.4. statystyki i procesy]]
[[3.5. Logi]]



kurs wideo
#helion #raźniewski_adam

**docker engine** pozwala uruchamiać kontenery
**kontener** mała uruchamialna paczka zawierająca jakąś aplikację (odizolowana od hosta)
**obraz** szablon do robienia kontenrów

instalacja:
`curl https://get.docker.com | bash`
git rancher -> różne rodzaje dockera

---
## warstwy
obraz jest zbiorem warst do odczytu 
np.
ubuntu - python
 |
java

strona `imagelayers.io`
microbadger -> pozwala zobaczyć ile warstw ma dany obraz

OBRAZY małe:
- alpine (linux)
- nginx (linux)
- httpd (apach) (uruchomienie w folderze z `index.html` wyświetli w przeglądarce stronę, dzięki `-v "$PWD:/usr/local/apache/htdocs ..."`)
- jenkins ()
- nextcloud (własna chmura danych)
- rocket chat























