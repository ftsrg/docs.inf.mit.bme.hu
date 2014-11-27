---
layout: page
title: Blogging Like a Hacker
header: Rendszermodellezés -- 2. gyakorlat -- megoldások
---

# Állapot alapú modellezés

## 1. feladat

Fogalmak:

* **Adatbázisszerver**: hosszútávon tároljuk az adatokat
* **Alkalmazásszerver**: az üzleti logikáért felelős alkalmazást futtatja
* **Webszerver**: megjelenítést felelős, generálja a HTML oldalakat

Válaszok:

1. Nem. A három közül *pontosan egynek* kell igaznak lennie minden időpillanatban.
1. Nem. Egyszerre több gép is dolgozhat.
1. Igen. Természetesen elképzelhetők további állapotok is, pl. *hibernált*.
1. Igen, ez egy végtelen állapotteret eredményez. A kizárólagosság mellett fontos vizsgálni, hogy teljes-e. Pl. 3,5 vagy $-9$ kérés nem lehet a rendszerben, ezért teljes.
1. Igen, ha egyszerre egy kérés lehet a rendszerben. Ezzel azonban a modellünk nem lesz alkalmas terhelések vizsgálatára.
1. Igen, ez teljes és kizárólagos, ezért alkalmas állapotpartíciónak. Ez az állapotmentes modell. Állapotmentes protokollokat (pl. a HTTP-t) érdemes lehet így modellezni.

## 2. feladat

1. {piros, sárga, zöld, piros-sárga, villogó sárga, kikapcsolt}, röviden: $S = \{p, s, z, ps, \bar{s}, \emptyset\}$. Ez kizárólagos és teljes. A kezdeti állapot: $p$.
1. $S_p = \{p, \emptyset\}$, $S_s = \{s, \bar{s}, \emptyset\}$, $S_z = \{z, \emptyset\}$. Másik színű filccel érdemes berajzolni az egy és a három állapotváltozós modell közötti kapcsolatokat, pl.
   * $p$ esetén $S_p = \{p\}, S_s = \{\emptyset\}, S_z = \{\emptyset\}$
   * direkt szorzat: $S_p \times S_s \times S_z$, $2 \times 3 \times 2 = 12$ elemű lesz.

Ebből természetesen nem minden állapot fordul elő: $S \subset S_p \times S_s \times S_z$

Hello.

First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell
