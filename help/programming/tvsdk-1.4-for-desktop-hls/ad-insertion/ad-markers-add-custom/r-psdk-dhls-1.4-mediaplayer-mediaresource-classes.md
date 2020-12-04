---
description: MediaResource représente le contenu qui est sur le point d’être chargé par l’instance MediaPlayer.
seo-description: MediaResource représente le contenu qui est sur le point d’être chargé par l’instance MediaPlayer.
seo-title: Classes MediaPlayer et MediaResource
title: Classes MediaPlayer et MediaResource
uuid: 36ef75f3-08f7-4fc5-88a7-9bab9198b917
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# classes MediaPlayer et MediaResource{#mediaplayer-and-mediaresource-classes}

MediaResource représente le contenu qui est sur le point d’être chargé par l’instance MediaPlayer.

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

La bibliothèque TVSDK fournit un moyen simple de charger et de préparer le contenu pour la lecture en utilisant la méthode `replaceCurrentResource` dans l&#39;interface `MediaPlayer`. Cette méthode reçoit une instance de la classe `MediaResource` en tant qu&#39;argument d&#39;entrée unique. La classe `MediaResource` est composée des informations suivantes :

* URL, qui représente l’emplacement du contenu sur le point d’être chargé.
* Type, qui correspond au type de contenu sur le point d’être chargé.

   Il s&#39;agit d&#39;une chaîne qui définit les types de contenu qui peuvent être chargés par `MediaPlayer`. Les valeurs possibles sont HLS et HDS. Chaque valeur est associée à la chaîne représentant les extensions de fichier couramment utilisées, &quot;m3u8&quot; pour HLS et &quot;f4m&quot; pour HDS.
* Certaines métadonnées, qui est une instance de la classe `Metadata`.

   Cette structure de type dictionnaire peut contenir des informations supplémentaires sur le contenu sur le point d’être chargé, telles que des informations sur le contenu alternatif/publicitaire à placer dans le contenu principal.

Les métadonnées sont le support par lequel les informations liées à un autre contenu sont transmises à TVSDK. L&#39;interface `Metadata` définit l&#39;API d&#39;un magasin de valeurs clés génériques, où la clé et la valeur sont des chaînes simples.
