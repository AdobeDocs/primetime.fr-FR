---
description: La fonction PABI (Partial Ad Break Insertion) imite une expérience de type TV dans laquelle, si l’utilisateur rejoint un flux en direct au sein d’une coupure de type mid-roll, des publicités mid-roll sont affichées à l’écran au lieu d’une publicité preroll ou d’une ardoise.
seo-description: La fonction PABI (Partial Ad Break Insertion) imite une expérience de type TV dans laquelle, si l’utilisateur rejoint un flux en direct au sein d’une coupure de type mid-roll, des publicités mid-roll sont affichées à l’écran au lieu d’une publicité preroll ou d’une ardoise.
seo-title: Insertion partielle de saut de publicité
title: Insertion partielle de saut de publicité
uuid: a0c1ae34-0f8d-4401-97fe-45a2ea40d08d
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Insertion partielle de saut de publicité {#partial-ad-break-insertion}

La fonction PABI (Partial Ad Break Insertion) imite une expérience de type TV dans laquelle, si l’utilisateur rejoint un flux en direct au sein d’une coupure de type mid-roll, des publicités mid-roll sont affichées à l’écran au lieu d’une publicité preroll ou d’une ardoise.

Lorsque le serveur d’annonces renvoie des publicités preroll pour un flux en direct, le serveur de manifeste injecte la coupure publicitaire preroll avant le point en direct et insère la balise EXT-X- avec sa valeur TIMEOFFSET pointant vers le de la coupure publicitaire preroll. Ce comportement par défaut garantit que la coupure publicitaire preroll complète est lue avant le contenu au point de production. Si un utilisateur rejoint un flux alors que le point de diffusion se trouve près d’une coupure publicitaire preroll moyenne, la coupure publicitaire preroll est présentée à l’utilisateur avant la coupure publicitaire mid-roll au point de production.

La fonction PABI indique au serveur de manifeste d’ignorer la coupure publicitaire preroll et de définir la valeur EXT-X-:TIMEOFFSET au début de la publicité mid-roll présente au point de production. Ainsi, l’utilisateur voit la totalité de la publicité mid-roll en cours de lecture au point de production sans avoir à  la coupure publicitaire pre-roll.

>[!NOTE]
>
>Cette fonctionnalité est disponible uniquement pour les flux en direct. Le serveur de manifeste insère par défaut la coupure publicitaire preroll au-dessus de la liste de lecture VOD.

>[!NOTE]
>
>Pour activer PABI, vous devez spécifier _params [](../../msapi-topics/ms-getting-started/ms-api-query-params.md) dans l’URL d’amorçage.

>[!NOTE]
>
>La EXT-X- [](https://tools.ietf.org/html/rfc8216#section-4.3.5.2) est une balise HLS standard qui indique un point de départ privilégié dans la liste de lecture.

## Recommandations {#section_4CF0733B14504F2A99690310B9F3B130}

* Utilisez le suivi côté client car le client dispose d’un meilleur contrôle sur le déclenchement des balises de suivi.
* Les coupures publicitaires partielles ne doivent être utilisées avec le mode de suivi côté serveur que si le lecteur prend en charge EXT-X-.