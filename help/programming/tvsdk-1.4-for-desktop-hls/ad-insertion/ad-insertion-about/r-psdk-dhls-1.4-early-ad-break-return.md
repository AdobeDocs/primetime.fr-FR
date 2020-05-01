---
description: Pour l’insertion de publicités en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.
seo-description: Pour l’insertion de publicités en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.
seo-title: Mise en oeuvre d’un retour anticipé de coupures publicitaires
title: Mise en oeuvre d’un retour anticipé de coupures publicitaires
uuid: 984b6ed0-c929-49a3-9553-e30d1a7758ed
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise en oeuvre d’un retour anticipé de coupures publicitaires{#implementing-an-early-ad-break-return}

Pour l’insertion de publicités en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.

>[!NOTE] {othertype=&quot;Condition préalable&quot;}
>
>Vous devez vous abonner aux marqueurs d’affichage/d’affichage publicitaire ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`et `#EXT-X-CUE`).

Voici quelques éléments à prendre en compte :

* Analyser les marqueurs tels que `EXT-X-CUE-IN` (ou balise de marqueur équivalente) qui apparaissent dans les flux linéaires ou FER.

   Enregistrez les marqueurs comme étant le marqueur du point de retour anticipé. Lecture uniquement `adBreaks` jusqu’à ce que cette position du marqueur soit définie pendant la lecture, ce qui remplace la durée du `adBreak` marqueur par le marqueur `EXE-X-CUE-OUT` de début.

* S’il existe deux `EXT-X-CUE-IN` marqueurs pour le même `EXT-X-CUE-OUT` marqueur, le premier `EXT-X-CUE-IN` marqueur qui s’affiche est celui qui compte.

* Si le `EXE-X-CUE-IN` marqueur apparaît dans le plan de montage chronologique sans `EXT-X-CUE-OUT` marqueur de début, le marqueur `EXE-X-CUE-IN` est ignoré.

   Dans un flux en direct, si le marqueur principal vient de sortir de la fenêtre, TVSDK ne lui répondra pas. `EXT-X-CUE-OUT`

* En cas de retour anticipé d’une coupure publicitaire, la `adBreak` lecture se produit jusqu’à ce que le curseur de lecture revienne à la position d’origine lorsque la coupure publicitaire devait se terminer et reprend la lecture du contenu principal à partir de cette position.

## SpliceOut et SpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` et `SpliceIn` les marqueurs marquent le début et la fin de la coupure publicitaire. La durée du `SpliceOut` type du `EXE-X-CUE` marqueur peut être égale à zéro et le `SpliceIn` type du marqueur `EXE-X-CUE` marque la fin de la coupure publicitaire. Elles apparaissent dans une balise et diffèrent par type.

**Un marqueur avec différents types**

Par exemple, voici un marqueur de différents types :

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

Dans l’exemple d’un marqueur de différents types, si la durée du `SpliceOut` type est égale à zéro, le marqueur `SpliceOut` et `SpliceIn` doivent fonctionner ensemble pour chaque coupure publicitaire. Actuellement, un `SpliceOut` marqueur d’une durée non nulle et n’ayant pas besoin de `SpliceIn` marqueurs d’appariement est plus typique.

**Deux marqueurs distincts**

Le scénario le plus courant est un `SpliceOut` marqueur de durée non nulle qui n’a pas besoin des `SpliceIn` marqueurs d’appariement. Ici, un `SpliceIn` marqueur d’appariement marque la fin de la coupure publicitaire pendant la lecture de la coupure publicitaire, mais la coupure publicitaire est raccourcie à la position du `SpliceIn` marqueur et les principaux débuts de contenu jouent à cette position.

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

