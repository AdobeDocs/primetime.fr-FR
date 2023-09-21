---
description: Une ressource MediaResource représente le contenu sur le point d’être chargé par l’instance MediaPlayer.
title: Classes MediaPlayer et MediaResource
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Classes MediaPlayer et MediaResource{#mediaplayer-and-mediaresource-classes}

Une ressource MediaResource représente le contenu sur le point d’être chargé par l’instance MediaPlayer.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

La bibliothèque TVSDK fournit un moyen simple de charger et de préparer le contenu pour la lecture à l’aide de la fonction `replaceCurrentItem` dans l’interface de MediaPlayer. Cette méthode reçoit une instance de la classe MediaResource en tant qu’argument d’entrée unique. La classe MediaResource est composée des informations suivantes :

* Une URL qui représente l’emplacement du contenu sur le point d’être chargé.
* Un type, qui est le type de contenu sur le point d’être chargé.

  Il s’agit d’une énumération simple dans la variable `MediaResource` qui définit les types de contenu pouvant être chargés par MediaPlayer. Les valeurs possibles sont HLS et HDS. Chaque valeur est associée à la chaîne représentant les extensions de fichier couramment utilisées, `m3u8` pour HLS et `f4m` pour HDS.
* Certaines métadonnées, qui est une instance de la variable `Metadata` classe .

  Cette structure de type dictionnaire peut contenir des informations supplémentaires sur le contenu sur le point d’être chargé, telles que des informations sur le contenu alternatif/publicitaire à placer dans le contenu principal.

Les métadonnées sont le moyen par lequel les informations liées au contenu alternatif sont transmises à TVSDK. La variable `Metadata` L’interface définit l’API d’un magasin de valeurs de clé générique, où la clé et la valeur sont des chaînes simples.
