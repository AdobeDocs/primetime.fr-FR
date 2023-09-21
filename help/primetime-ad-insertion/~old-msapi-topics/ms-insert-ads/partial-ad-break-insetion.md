---
description: La fonctionnalité d’insertion de coupure publicitaire partielle (PABI) imite une expérience de type TV dans laquelle, si l’utilisateur rejoint une diffusion en direct au cours d’une coupure mid-roll, l’utilisateur est affiché dans des publicités mid-roll au lieu d’une publicité preroll ou d’une ardoise.
title: Insertion de coupure publicitaire partielle
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Insertion de coupure publicitaire partielle {#partial-ad-break-insertion}

La fonctionnalité d’insertion de coupure publicitaire partielle (PABI) imite une expérience de type TV dans laquelle, si l’utilisateur rejoint une diffusion en direct au cours d’une coupure mid-roll, l’utilisateur est affiché dans des publicités mid-roll au lieu d’une publicité preroll ou d’une ardoise.

Lorsque le serveur de publicités renvoie des publicités preroll pour un flux en direct, le serveur de manifeste injecte la coupure publicitaire preroll avant le point en direct et insère la balise EXT-X-START avec sa valeur TIMEOFFSET indiquant le début de la coupure publicitaire preroll. Ce comportement par défaut garantit que la coupure publicitaire preroll complète est lue avant le contenu au point d’activation. Si un utilisateur rejoint un flux alors que le point d’entrée en direct est proche d’une coupure publicitaire mid-roll, la coupure publicitaire preroll est présentée à l’utilisateur avant la coupure publicitaire mid-roll au point d’entrée en direct.

La fonction PABI indique au serveur de manifeste d’ignorer la coupure publicitaire preroll et de définir la valeur EXT-X-START:TIMEOFFSET sur le début de la publicité mid-roll présente au point de production. Cela permet à l’utilisateur de voir l’intégralité de la publicité mid-roll en cours de lecture au point d’activation sans avoir à afficher la coupure publicitaire preroll.

>[!NOTE]
>
>Cette fonctionnalité est disponible uniquement pour les diffusions en direct. Le serveur de manifeste insère par défaut la coupure publicitaire preroll au-dessus de la liste de lecture VOD.

>[!NOTE]
>
>Pour activer PABI, vous devez spécifier la variable [query_params](/help/primetime-ad-insertion/~old-msapi-topics/ms-getting-started/ms-api-query-params.md) dans l’URL de bootstrap.

>[!NOTE]
>
>La variable [EXT-X-START](https://tools.ietf.org/html/rfc8216#section-4.3.5.2) est une balise HLS standard qui indique un point de départ préféré dans la liste de lecture.

## Recommendations {#section_4CF0733B14504F2A99690310B9F3B130}

* Utilisez le suivi côté client, car le client a plus de contrôle sur le déclenchement des balises de suivi.
* Les coupures publicitaires partielles ne doivent être utilisées avec le mode de suivi côté serveur que si le lecteur prend en charge EXT-X-START.