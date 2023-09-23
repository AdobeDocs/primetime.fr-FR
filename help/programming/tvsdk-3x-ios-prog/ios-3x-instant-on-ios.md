---
description: Instant-on précharge des parties du média sur un ou plusieurs canaux. Une fois qu’un utilisateur sélectionne ou change de canal, le contenu commence plus tôt, car une partie de la mise en mémoire tampon est déjà terminée.
title: Instant
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Instant {#instant-on}

Instant-on précharge des parties du média sur un ou plusieurs canaux. Une fois qu’un utilisateur sélectionne ou change de canal, le contenu commence plus tôt, car une partie de la mise en mémoire tampon est déjà terminée.

Lorsque votre lecteur se trouve dans la variable `PTMediaPlayerStatusReady` status, appel `prepareToPlay` pour précharger et traiter une partie du contenu en vue d’une lecture ultérieure.

>[!TIP]
>
>Si vous n’appelez pas `prepareToPlay`, appel `play` appels automatiques `prepareToPlay` en premier. Le préchargement et le traitement sont terminés à ce stade.

TVSDK effectue certaines ou toutes les tâches suivantes pour `prepareToPlay`:

* Si la clé de métadonnées `kSyncCookiesWithAVAsset` est défini, TVSDK émet une requête au fichier M3U8 d’origine pour synchroniser les cookies.
* Charge les clés de métadonnées DRM.
* Crée et prépare certaines structures, éléments ou ressources nécessaires à la lecture de contenu.

>[!TIP]
>
>La variable `PTMediaPlayer` et `PTMediaPlayerItem` `prepareToPlay` sont égales. Pour éviter de créer une `PTMediaPlayer` pour chaque ressource, utilisez la méthode `PTMediaPlayerItem` .

Instant-on vous permet de lancer plusieurs instances de lecteur multimédia, ou instances de chargeur d’éléments du lecteur multimédia, simultanément en arrière-plan et dans la mémoire tampon des diffusions vidéo dans toutes ces instances. Lorsqu’un utilisateur modifie le canal et que la diffusion a été mise en mémoire tampon correctement, l’appel de la fonction `play` sur le nouveau canal, la lecture démarre plus tôt.
