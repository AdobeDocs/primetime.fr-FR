---
description: Instant-on précharge des parties du média sur un ou plusieurs canaux. Une fois qu’un utilisateur sélectionne ou change de canal, le contenu début plus tôt car une partie de la mise en mémoire tampon est déjà terminée.
seo-description: Instant-on précharge des parties du média sur un ou plusieurs canaux. Une fois qu’un utilisateur sélectionne ou change de canal, le contenu début plus tôt car une partie de la mise en mémoire tampon est déjà terminée.
seo-title: Instant-on
title: Instant-on
uuid: 98a5ef79-51e4-474e-a6e8-ca449c430b5e
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Instant {#instant-on}

Instant-on précharge des parties du média sur un ou plusieurs canaux. Une fois qu’un utilisateur sélectionne ou change de canal, le contenu début plus tôt car une partie de la mise en mémoire tampon est déjà terminée.

Lorsque votre lecteur est à l’état `PTMediaPlayerStatusReady`, appelez `prepareToPlay` pour précharger et traiter une partie du contenu en vue d’une lecture ultérieure.

>[!TIP]
>
>Si vous n&#39;appelez pas `prepareToPlay`, l&#39;appel de `play` appelle automatiquement `prepareToPlay` en premier. Le préchargement et le traitement sont terminés pour le moment.

TVSDK complète certaines ou la totalité des tâches suivantes pour `prepareToPlay` :

* Si la clé de métadonnées `kSyncCookiesWithAVAsset` est définie, TVSDK émet une requête au fichier M3U8 d’origine pour synchroniser les cookies.
* Charge les clés de métadonnées DRM.
* Crée et prépare certaines structures, éléments ou ressources nécessaires à la lecture du contenu.

>[!TIP]
>
>Les méthodes `PTMediaPlayer` et `PTMediaPlayerItem` `prepareToPlay` sont égales. Pour éviter de créer une instance `PTMediaPlayer` distincte pour chaque ressource, utilisez la méthode `PTMediaPlayerItem`.

Instant-on vous permet de lancer simultanément plusieurs instances de lecteur de médias ou de chargeur d’élément de lecteur de médias en arrière-plan et de mettre en mémoire tampon les flux vidéo dans toutes ces instances. Lorsqu’un utilisateur modifie le canal et que le flux est mis en mémoire tampon correctement, l’appel à `play` sur le nouveau canal début la lecture plus tôt.