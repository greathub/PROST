# Grafana Loki - szybciutki start

W celu szybkiego zainstalowania Grafany z Loki, musisz mieć [`gita`](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) oraz [`docker-compose`](https://docs.docker.com/compose/install/) zainstalowanego na swojej maszynie. Możesz też skorzystać z innych dostępnych metod na oficjalnej [stronie Grafany](https://grafana.com/docs/loki/latest/installation/).

## Instalacja
Najpierw ściągnij repozytorium Loki z ich oficjalnego githuba:
```shell script
git clone https://github.com/grafana/loki.git
```
Następnie zmień scieżkę na produkcyjną, która zawiera pliki yamal docker-compose.
```shell script
cd loki/production
```
Pobierz obrazy:
```shell script
docker-compose pull
```
Uruchom instancję:
```shell script
docker-compose up
```
## Konfiguracja
1) Jeżeli pomyślnie udało Ci się zainstalować, przejdź do przeglądarki odpalając Grafanę na swoim hoście:
[`http://localhost:3000`](http://localhost:3000)

2) Następnie zaloguj się używając login `admin` i hasło `admin`. 

3) Po zalogowaniu, najedź na ikonkę kół zębatych ⚙️ i kliknij `Data Sources`.
Teraz możesz wybrać typy danych, które chcesz dodać do Grafany.

4) Wybieramy `Add data source` a następnie znajdujemy i klikamy w pozycję `Loki`.

5) Będąc na stronie konfiguracji musimy dodać URL serwera loki, który aktualnie jest na naszym hoście. 
Wpisujemy więc `http://loki:3100` i klikamy `Save and Test`.

![](img/add-loki.gif)

## Eksploracja


## Instalacja pluginów
Znajdź interesujący Cię plugin na [bazarku Grafany](https://grafana.com/grafana/plugins):

Aby zainstalować plugin z marketplace możesz zrobić to poprzez terminal. W tym celu znajdź id kontenera Grafany:
```shell script
docker ps
```

A następnie uruchom bash w tym kontenerze:
```shell script
docker exec -it  bash
```

Zainstaluj znaleziony wcześniej [plugin](https://grafana.com/grafana/plugins/innius-video-panel/):
```shell script
grafana-cli plugins install innius-video-panel
```

Opuść kontener i zrestartuj go (można alternatywnie odpowiedni serwis w kontenerze):
```shell script
exit
docker restart <ID-KONTENERA-TU>
```

## Źródła
Powyższa instrukcja została zainspirowana następującymi źródłami:
1) ▶️[Getting started with Grafana Loki - under 4 minutes](https://www.youtube.com/watch?v=1obKa6UhlkY)
2) 📰 [Grafana Loki Intro](https://geekflare.com/grafana-loki-intro/)
3) 📰 [Open source centralized logging](https://geekflare.com/open-source-centralized-logging/)
4) 📰 [Another link to verify](https://opensource.com/article/18/9/open-source-log-aggregation-tools)
5) 📰 [Oficial github](https://github.com/grafana/loki)
6) 📰 [Dokumentacja Loki](https://grafana.com/docs/loki/latest)
7) 📰 [How labels works in Loki](https://grafana.com/blog/2020/08/27/the-concise-guide-to-labels-in-loki/)


Przydatne linki do Grafany i jej dokumentacji:
1) [Dokumentacja Grafany](https://grafana.com/docs/grafana/latest/)
2) [Bazarek Dashboardów](https://grafana.com/grafana/dashboards)
3) [Bazarek Pluginów](https://grafana.com/grafana/plugins/)
3) [Instalacja pluginów](https://grafana.com/docs/grafana/latest/administration/cli/#plugins-commands)
