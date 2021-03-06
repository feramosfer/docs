---
title: Konfiguracja automatycznego usuwania obiektów
excerpt: Konfiguracja automatycznego usuwania obiektów
slug: konfiguracja_automatycznego_usuwania_obiektow
section: Object Storage
legacy_guide_number: g1950
---


## 
Aby uprościć zarządzanie usługą Object Storage, być może będziesz musiał zadecydować o długości życia niektórych plików. 
Może to na przykład pozwolić Ci na zachowanie niektórych kopii zapasowych tylko przez określony czas. 
Przewodnik ten wyjaśnia, jak usuwać pliki w sposób automatyczny po określonym czasie lub w określonym terminie.


## Wstępne wymagania

- [Przygotowanie środowiska do korzystania z API OpenStack]({legacy}1851)
- [Pobieranie zmiennych środowiskowych OpenStack]({legacy}1852)




## 
Istnieją 2 sposoby usuwania plików:

- Po określonym czasie
- W określonym terminie




## Po określonym czasie
Aby to wykonać, należy skonfigurować header X-Delete-After dla obiektów:


```
root@server:~$ swift post --header "X-Delete-After: 3600" container test.txt
```


Plik test.txt zostanie usunięty po 1 godzinie.


## W określonym terminie
Najpierw trzeba poznać datę usunięcia w formacie epoch.
Można korzystać z [konwertera](http://www.epochconverter.com/), aby sprawdzić wartość do wpisania. 

Następnie można wpisać tę datę w nagłówku (header) X-Delete-At:


```
root@server:~$ swift post --header "X-Delete-At: 1448928000000" container test.txt
```


Plik test.txt zostanie usunięty 01 grudnia 2015 roku.


## 
[Przewodniki Cloud]({legacy}1785)

