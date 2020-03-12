---
description: Vous pouvez insérer des publicités dans votre contenu VOD et le contenu dynamique/linéaire à l’aide de l’interface de prise de décision publicitaire d’Adobe Primetime.
seo-description: Vous pouvez insérer des publicités dans votre contenu VOD et le contenu dynamique/linéaire à l’aide de l’interface de prise de décision publicitaire d’Adobe Primetime.
seo-title: Conditions requises pour la publicité
title: Conditions requises pour la publicité
uuid: 0287f1e4-746f-42e5-b811-409064dd9b13
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Conditions requises pour la publicité {#advertising-requirements}

Vous pouvez insérer des publicités dans votre contenu VOD et le contenu dynamique/linéaire à l’aide de l’interface de prise de décision publicitaire d’Adobe Primetime.

<!--<a id="section_A2966DC850E140FE9400A1D9E412F819"></a>-->

La prise de décision publicitaire Primetime fonctionne avec TVSDK pour identifier les opportunités publicitaires, résoudre les publicités et insérer des publicités résolues dans vos flux vidéo.

Pour incorporer des publicités dans votre contenu vidéo, assurez-vous que la publicité et le contenu vidéo principal répondent aux exigences suivantes :

* La version HLS du contenu publicitaire ne peut pas être supérieure à la version HLS du contenu principal.
* Les publicités doivent être multiplexées et doivent contenir un rendu audio uniquement, que le contenu principal soit multiplexé ou non.
* Les listes de lecture des publicités doivent avoir les mêmes rendus de débit binaire que les rendus de la liste de lecture du contenu principal.
* La durée de  du et la durée des fragments individuels d’une publicité ne peuvent pas dépasser la durée de  du contenu principal.
* Si le contenu principal contient un flux audio uniquement, le contenu publicitaire doit également contenir un flux audio uniquement.
* Si le contenu principal contient des flux de sous-titres, le contenu publicitaire doit être non chiffré.
* Si le contenu principal est à débit binaire multiple (MBR), le contenu publicitaire doit également être MBR.
* Si le contenu principal comporte d’autres pistes audio, chaque publicité doit comporter au moins un flux audio uniquement.

Si la publicité ne comporte pas au moins un flux audio uniquement, elle est ignorée.