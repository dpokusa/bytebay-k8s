# Kubernetes od podstaw

## Wprowadzenie

W świecie systemów rozproszonych, mikrousług, zdarzeń programiście nie wystarczy już tylko wiedzieć jak napisać i zbudować kod źródłowy. W świecie, w którym system podzielony jest na kilka, kilkanaście, kilkadziesiąt lub kilkaset modułów przychodzi taki moment w którym potrzebujemy skomunikować się z innymi komponentami.

W tym samym świecie systemy produkcyjnie uruchamiamy w chmurze. I wszystko ładnie, pięknie, ale jak tutaj prowadzić development? Czy każdy programista powinien mieć swoją chmurę na którą będzie w stanie wrzucić swoje "dziecko w trakcie aktu tworzenia"? Czy musimy uruchamiać wszystko? Co z kosztem? W takim razie może powinienem uruchamiać swoją lokalną instancję poza chmurą? Ale czy wtedy nie istnieje ryzyko, że inny sposób wdrożenia podczas developmentu spowoduje problemy na środowiskach produkcyjnych?

A może by tak dało się prościej? Może da się tworzyć w oparciu o takie same podejście do wdrożeń na lokalnej maszynie programisty z możliwością wybrania, które elementy faktycznie powinny zostać uruchomione? Może development mógłby działać podobnie do produkcji i gwarantować taki sam sposób wdrożenia?

Chciałbym Wam pokazać jedną z alternatyw- podejście które jest wygodne zarówno od strony OPSów jak i programistów, podejście, które potrafi bardzo przyspieszyć i ułatwić development. Podejście, które pozwoli nam (programistom) i administratorom wejść w świat kultury devops i naprawdę lepiej rozumieć siebie nawzajem.

**W ramach warsztatów:**

* Skonfigurujesz poprawnie lokalne środowisko pracy z kubernetesem
* Na podstawie przygotowanych i udostępnionych obrazów dockera przykładowych aplikacji wdrożysz własne moduły na kilka różnych sposobów wraz z wyróżnieniem wad i zalet każdego z podejść
* Opracujesz automatyczny restart aplikacji na wypadek problemów i zobaczysz jak działa to w praktyce
* Skonfigurujesz na potrzeby developmentu bazy danych i inne usługi serwisowe
* Zdefiniujesz automatyczne skalowanie aplikacji
* Przeprowadzisz rolling-release przykładowej aplikacji gwarantując tzw. "zero-downtime"
* Dowiesz się jak rekonfigurować aplikację za pomocą config map
* Zabezpieczysz hasła i klucze do baz danych

Wszystko to pozwoli Ci swobodnie pracować i przygotowywać konfiguracje aplikacji za które administratorzy Cię pokochają :)

**Wymagania**

* Komputer z minimum 8GB pamięci (mocno zalecane 12GB) i procesor z minimum dwoma core'ami
* Skonfigurowany i zainstalowany docker (https://docs.docker.com/install/)
* Podstawowa znajomość komend dockera (pobieranie obrazów z dockerhub, budowanie obrazów). Znajomość przygotowywania plików dockera może pomóc, ale nie jest konieczna.
* Zainstalowany edytor tekstu
* Konsola użytkownika i podstawowa umiejętność jej obsługi w swoim systemie operacyjnym
* Dodatkowa instalacja minikube mile widziana: https://github.com/kubernetes/minikube

## Instalacja minikube

## Linux

* https://github.com/kubernetes/minikube

## Windows

* https://medium.com/@JockDaRock/minikube-on-windows-10-with-hyper-v-6ef0f4dc158c

# Warsztaty

## Zanim zaczniemy

Zaraz po pobraniu tego repozytorium i ewentualnej instalacji minikube odpalamy:

### Linux

`minikube start -vm 4000`

### Windows

W wypadku hyper-V:

`minikube start --vm-driver hyperv --hyperv-virtual-switch "Primary Virtual Switch"`

Gdzie `"Primary Virtual Swtich"` to stworzony wirtualny przełącznik.

## Zaczynamy!

