---
title: Transcodage juste à temps
description: null
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# Transcodage juste à temps {#just-in-time-transcoding}

L’Ad Insertion Primetime dispose d’un transcodage et d’un pack juste-à-temps pour garantir que les éléments créatifs publicitaires incompatibles peuvent être correctement lus dans les flux de contenu. Il peut également injecter des paquets ID3 dans des fragments publicitaires qui peuvent être utilisés dans le suivi des publicités côté client.
Voici un flux de travaux type :

1. L’Ad Insertion Adobe Primetime récupère les publicités/éléments créatifs du serveur d’annonces du client.

1. Si le format créatif d’une publicité est nativement compatible avec le flux de contenu, la création est insérée dans le manifeste.

1. Si le format créatif d’une publicité n’est pas compatible nativement (par exemple, .mp4, .mov, .webm), l’Ad Insertion Primetime recherche une version précodée de la publicité à partir d’un réseau de diffusion de contenu spécifié. Si une publicité est trouvée, elle est insérée ; sinon, la publicité est mise en file d’attente pour transcoder.

1. Une fois que le créatif de la publicité est transcodé, l’Ad Insertion Primetime rassemble toutes les requêtes suivantes pour cette ressource publicitaire dans les manifestes.

L’Ad Insertion Primetime prend en charge le transcodage pour la plupart des formats vidéo et linéaires. Le transcodage publicitaire créatif se produit généralement en moins de trois minutes. Pour plus d&#39;informations, veuillez contacter votre représentant de l&#39;assistance technique de Primetime.
