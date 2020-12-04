---
description: La fonction d’insertion de coupures publicitaires partielles (PABI) imite une expérience de type TV dans laquelle, si l’utilisateur rejoint un flux en direct au cours d’une coupure intermédiaire, des publicités intermédiaires sont affichées à l’écran plutôt qu’une publicité preroll ou une ardoise.
seo-description: La fonction d’insertion de coupures publicitaires partielles (PABI) imite une expérience de type TV dans laquelle, si l’utilisateur rejoint un flux en direct au cours d’une coupure intermédiaire, des publicités intermédiaires sont affichées à l’écran plutôt qu’une publicité preroll ou une ardoise.
seo-title: Insertion partielle de coupures publicitaires
title: Insertion partielle de coupures publicitaires
uuid: a0c1ae34-0f8d-4401-97fe-45a2ea40d08d
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Insertion de coupures publicitaires partielles {#partial-ad-break-insertion}

La fonction d’insertion de coupures publicitaires partielles (PABI) imite une expérience de type TV dans laquelle, si l’utilisateur rejoint un flux en direct au cours d’une coupure intermédiaire, des publicités intermédiaires sont affichées à l’écran plutôt qu’une publicité preroll ou une ardoise.

Lorsque le serveur d’annonces renvoie des publicités preroll pour un flux en direct, le serveur de manifeste injecte la coupure publicitaire preroll avant le point en direct et insère la balise EXT-X-DÉBUT avec sa valeur TIMEOFFSET pointant vers le début de la coupure publicitaire preroll. Ce comportement par défaut permet de s’assurer que la coupure publicitaire preroll complète est lue avant le contenu au point de production. Si un utilisateur rejoint un flux alors que le point de diffusion est proche d’une coupure publicitaire intermédiaire, la coupure publicitaire preroll s’affiche avant la coupure publicitaire intermédiaire au point de diffusion réel.

La fonction PABI indique au serveur de manifeste d’ignorer la coupure publicitaire preroll et de définir la valeur EXT-X-DÉBUT:TIMEOFFSET sur le début de la publicité mid-roll présente au point de production. Ainsi, l’utilisateur voit la totalité de la publicité preroll en cours de lecture au point de production sans avoir à vue la coupure publicitaire preroll.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour les flux en direct. Le serveur de manifeste insère par défaut la coupure publicitaire preroll au-dessus de la liste de lecture VOD.

>[!NOTE]
>
>Pour activer PABI, vous devez spécifier [requête_params](../../msapi-topics/ms-getting-started/ms-api-query-params.md) dans l’URL d’amorçage.

>[!NOTE]
>
>[EXT-X-DÉBUT](https://tools.ietf.org/html/rfc8216#section-4.3.5.2) est une balise HLS standard qui indique un point de départ privilégié dans la liste de lecture.

## Recommendations {#section_4CF0733B14504F2A99690310B9F3B130}

* Utilisez le suivi côté client car le client dispose d’un meilleur contrôle sur le déclenchement des balises de suivi.
* Les coupures publicitaires partielles ne doivent être utilisées avec le mode de suivi côté serveur que si le lecteur prend en charge le DÉBUT EXT-X.