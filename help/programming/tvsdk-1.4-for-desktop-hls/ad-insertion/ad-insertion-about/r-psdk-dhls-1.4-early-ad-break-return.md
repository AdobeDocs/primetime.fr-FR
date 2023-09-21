---
description: Pour l’insertion de publicités en continu, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.
title: Mise en oeuvre d’un retour de coupure publicitaire anticipée
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Mise en oeuvre d’un retour de coupure publicitaire anticipée{#implementing-an-early-ad-break-return}

Pour l’insertion de publicités en continu, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.

>[!NOTE]
>
>Vous devez vous abonner aux marqueurs d’annonce sortants/intégrés ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`, et `#EXT-X-CUE`).

Voici quelques conditions à prendre en compte :

* Marqueurs d’analyse tels que `EXT-X-CUE-IN` (ou balise de marqueur équivalente) qui apparaissent dans les flux linéaires ou FER.

  Enregistrez les marqueurs comme étant le marqueur du point de retour anticipé de la publicité. Lecture seule `adBreaks` jusqu’à cette position du marqueur pendant la lecture, qui remplace la durée de la variable `adBreak` marqué par le début `EXE-X-CUE-OUT` marqueur.

* Si deux `EXT-X-CUE-IN` Il existe des marqueurs pour le même `EXT-X-CUE-OUT` marqueur, le premier `EXT-X-CUE-IN` qui apparaît est celui qui compte.

* Si la variable `EXE-X-CUE-IN` apparaît dans la chronologie sans balise `EXT-X-CUE-OUT` , le marqueur `EXE-X-CUE-IN` est ignoré.

  Dans une diffusion en direct, si la variable `EXT-X-CUE-OUT` Le marqueur vient de sortir de la fenêtre, TVSDK n’y répondra pas.

* En cas de retour anticipé d’une coupure publicitaire, la variable `adBreak` est lu jusqu’à ce que le curseur de lecture revienne à la position d’origine lorsque la coupure publicitaire était censée se terminer et reprend la lecture du contenu principal à partir de cette position.

## SpliceOut et SpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` et `SpliceIn` les marqueurs indiquent le début et la fin de la coupure publicitaire. La durée de la variable `SpliceOut` type de `EXE-X-CUE` Le marqueur peut être égal à zéro et la variable `SpliceIn` type de `EXE-X-CUE` marque la fin de la coupure publicitaire. Elles apparaissent dans une balise et diffèrent par type.

**Un marqueur avec différents types**

Par exemple, voici un marqueur avec différents types :

```
#EXTM3U#EXT-X-TARGETDURATION:10
#EXT-X-VERSION:3
#EXT-X-MEDIA-SEQUENCE:44
  
#EXTINF:9.9,
https://server-host/path/file44.ts
#EXTINF:4.2,
https://server-host/path/file45.ts
  
#EXT-X-CUE:TYPE="SpliceOut",ID="1",DURATION="0",TIME="266.198",PROGRAM-ID="138",AVAIL-NUM="1",AVAILS-EXPECTED="10"
#EXTINF:5.8,
https://server-host/path/file46.ts
#EXTINF:9.9,
https://server-host/path/file47.ts
...
#EXTINF:9.9,
https://server-host/path/file56.ts
#EXTINF:4.2,
https://server-host/path/file57.ts
#EXT-X-CUE:TYPE="SpliceIn",ID="1",DURATION="0",TIME="266.198",PROGRAM-ID="138"
#EXTINF:9.9,
https://server-host/path/file58.ts
```

Dans le marqueur avec différents types, par exemple, si la durée de la variable `SpliceOut` est égal à zéro, la variable `SpliceOut` et `SpliceIn` doit travailler ensemble pour chaque coupure publicitaire. Actuellement, une `SpliceOut` marqueur avec une durée non nulle et n’a pas besoin de couplage `SpliceIn` les marqueurs sont plus typiques.

**Deux marqueurs distincts**

Le scénario le plus courant est un scénario `SpliceOut` marqueur de durée non nulle qui n’a pas besoin de l’association `SpliceIn` marqueurs. Ici, un couplage `SpliceIn` Le marqueur marque la fin de la coupure publicitaire lors de la lecture de la coupure publicitaire, mais la coupure publicitaire est coupée court au niveau de `SpliceIn` position du marqueur et la lecture du contenu principal commence à cette position.

Par exemple, il existe deux marqueurs distincts :

```
#EXT-X-CUE-OUT:ID=105,DURATION=30.0,TIME=1081.08
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589090425811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589150485811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589210545811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589270605811,format=m3u8-aapl-v4)
#EXT-X-CUE-IN:ID=105,TIME=1105.104
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589330665811,format=m3u8-aapl-v4)
```
