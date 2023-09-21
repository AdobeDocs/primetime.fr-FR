---
title: Exigences publicitaires
description: Exigences publicitaires
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Exigences publicitaires {#advertising-requirements}

Vous pouvez insérer des publicités dans votre contenu VOD et linéaire à l’aide de l’interface de prise de décision publicitaire d’Adobe Primetime.

La prise de décision publicitaire Primetime fonctionne avec TVSDK pour identifier les opportunités publicitaires, résoudre les publicités et insérer les publicités résolues dans vos flux vidéo.

Pour incorporer des publicités dans votre contenu vidéo, assurez-vous que la publicité et le contenu vidéo principal répondent aux exigences suivantes :

* La version HLS du contenu publicitaire ne peut pas être supérieure à la version HLS du contenu principal.
* Les publicités doivent être multiplexées et doivent contenir un rendu audio uniquement, que le contenu principal soit multiplexé ou non.
* Les listes de lecture de publicités doivent avoir le même débit que les rendus de la liste de lecture du contenu principal.
* La durée cible et la durée de fragment d’une publicité ne peuvent pas dépasser la durée cible du contenu principal.
* Si le contenu principal contient un flux audio uniquement, le contenu publicitaire doit également contenir un flux audio uniquement.
* Si le contenu principal contient des flux de sous-titres, le contenu publicitaire doit être déchiffré.
* Si le contenu principal est à débit multiple (MBR), le contenu publicitaire doit également être MBR.
* Si le contenu principal comporte des pistes audio alternatives, chaque publicité doit comporter au moins une diffusion audio seule.

  Si la publicité ne comporte pas au moins un flux audio uniquement, elle est ignorée.
