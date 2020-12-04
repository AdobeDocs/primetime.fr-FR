---
description: MediaResource représente le contenu qui est sur le point d’être chargé par l’instance MediaPlayer.
seo-description: MediaResource représente le contenu qui est sur le point d’être chargé par l’instance MediaPlayer.
seo-title: Classes MediaPlayer et MediaResource
title: Classes MediaPlayer et MediaResource
uuid: 7393c320-7dbb-4580-9425-a735f9d03ef5
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# classes MediaPlayer et MediaResource{#mediaplayer-and-mediaresource-classes}

MediaResource représente le contenu qui est sur le point d’être chargé par l’instance MediaPlayer.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

La bibliothèque TVSDK fournit un moyen simple de charger et de préparer le contenu pour la lecture en utilisant la méthode `replaceCurrentItem` dans l’interface de MediaPlayer. Cette méthode reçoit une instance de la classe MediaResource en tant qu&#39;argument d&#39;entrée unique. La classe MediaResource se compose des informations suivantes :

* URL, qui représente l’emplacement du contenu sur le point d’être chargé.
* Type, qui correspond au type de contenu sur le point d’être chargé.

   Il s&#39;agit d&#39;une énumération simple de la classe `MediaResource` qui définit les types de contenu qui peuvent être chargés par MediaPlayer. Les valeurs possibles sont HLS et HDS. Chaque valeur est associée à la chaîne représentant les extensions de fichier couramment utilisées, `m3u8` pour HLS et `f4m` pour HDS.
* Certaines métadonnées, qui est une instance de la classe `Metadata`.

   Cette structure de type dictionnaire peut contenir des informations supplémentaires sur le contenu sur le point d’être chargé, telles que des informations sur le contenu alternatif/publicitaire à placer dans le contenu principal.

Les métadonnées sont le support par lequel les informations liées à un autre contenu sont transmises à TVSDK. L&#39;interface `Metadata` définit l&#39;API d&#39;un magasin de valeurs clés génériques, où la clé et la valeur sont des chaînes simples.
