---
description: Une ressource MediaResource représente le contenu qui est sur le point d’être chargé par l’instance MediaPlayer.
seo-description: Une ressource MediaResource représente le contenu qui est sur le point d’être chargé par l’instance MediaPlayer.
seo-title: Classes MediaPlayer et MediaResource
title: Classes MediaPlayer et MediaResource
uuid: 7393c320-7dbb-4580-9425-a735f9d03ef5
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Classes MediaPlayer et MediaResource{#mediaplayer-and-mediaresource-classes}

Une ressource MediaResource représente le contenu qui est sur le point d’être chargé par l’instance MediaPlayer.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

La bibliothèque TVSDK fournit un moyen simple de charger et de préparer le contenu pour la lecture à l’aide de la `replaceCurrentItem` méthode de l’interface de MediaPlayer. Cette méthode reçoit une instance de la classe MediaResource en tant qu’argument d’entrée unique. La classe MediaResource se compose des informations suivantes :

* URL qui représente l’emplacement du contenu sur le point d’être chargé.
* Type, qui correspond au type de contenu sur le point d’être chargé.

   Il s’agit d’un simple  de la `MediaResource` classe qui définit les types de contenu pouvant être chargés par le lecteur multimédia. Les valeurs possibles sont HLS et HDS. Chaque valeur est associée à la chaîne représentant les extensions de fichier couramment utilisées, `m3u8` pour HLS et `f4m` pour HDS.
* Certaines métadonnées, qui est une instance de la `Metadata` classe.

   Cette structure de type dictionnaire peut contenir des informations supplémentaires sur le contenu qui est sur le point d’être chargé, telles que des informations sur le contenu alternatif/publicitaire à placer dans le contenu principal.

Les métadonnées sont le support par lequel les informations liées au contenu alternatif sont transmises à TVSDK. L’ `Metadata` interface définit l’API d’un magasin de valeurs clés génériques, où la clé et la valeur sont des chaînes simples.
