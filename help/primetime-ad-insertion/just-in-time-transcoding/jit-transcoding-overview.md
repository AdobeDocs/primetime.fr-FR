---
title: Transcodage juste à temps
description: Transcodage juste à temps
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# Transcodage juste à temps {#just-in-time-transcoding}

Primetime Ad Insertion comprend un transcodage et un package juste à temps pour s’assurer que les créatifs publicitaires incompatibles peuvent être lus correctement dans les flux de contenu. Il peut également injecter des paquets ID3 dans des fragments de publicité qui peuvent être utilisés dans le suivi des publicités côté client.
Un workflow type est le suivant :

1. Adobe Primetime Ad Insertion récupère les publicités/éléments créatifs du serveur de publicités du client.

1. Si le format créatif d’une publicité est compatible en mode natif avec le flux de contenu, le contenu créatif est inséré dans le manifeste.

1. Si le format créatif d’une publicité n’est pas compatible en mode natif (par exemple, .mp4, .mov, .webm), l’Ad Insertion Primetime recherche une version précodée de la publicité à partir d’un réseau de diffusion de contenu spécifié. Si une publicité est trouvée, elle est insérée ; dans le cas contraire, elle est mise en file d’attente pour le transcodage.

1. Une fois le code de création publicitaire transcodé, l’Ad Insertion Primetime réunira toutes les demandes suivantes pour cette ressource publicitaire dans les manifestes.

L’Ad Insertion Primetime prend en charge le transcodage pour la plupart des formats vidéo et linéaire. Le transcodage créatif publicitaire se produit généralement en moins de trois minutes. Pour plus d’informations, contactez votre représentant de l’assistance Primetime.
