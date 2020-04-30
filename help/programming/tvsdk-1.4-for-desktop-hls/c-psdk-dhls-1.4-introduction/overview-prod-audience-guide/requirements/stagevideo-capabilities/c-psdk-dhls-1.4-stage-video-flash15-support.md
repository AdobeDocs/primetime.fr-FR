---
description: A partir de Flash 15 et versions ultérieures, lorsque le rendu matériel avec StageVideo n’est pas disponible, StageVideo revient en douceur à un objet StageVideo logiciel.
seo-description: A partir de Flash 15 et versions ultérieures, lorsque le rendu matériel avec StageVideo n’est pas disponible, StageVideo revient en douceur à un objet StageVideo logiciel.
seo-title: Prise en charge de Flash 15 pour StageVideo
title: Prise en charge de Flash 15 pour StageVideo
uuid: 49bd8703-016e-4fda-8773-5254d4774ec6
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Prise en charge de Flash 15 pour StageVideo{#flash-support-for-stagevideo}

A partir de Flash 15 et versions ultérieures, lorsque le rendu matériel avec StageVideo n’est pas disponible, StageVideo revient en douceur à un objet StageVideo logiciel.

Tenez compte des informations suivantes concernant la reprise de l’application StageVideo Flash 15 dans le logiciel :

* Aucune modification du code n’est requise dans votre application.
* Aucune modification apportée à TVSDK n’est requise.

   Vous n’avez pas besoin d’une mise à jour de TVSDK pour utiliser le logiciel de secours StageVideo.
* Vos applications doivent être recompilées pour Flash 15.
* Les applications que vous recompilez pour Flash 15 continueront à fonctionner avec Flash 14 et les versions antérieures, à condition que ces applications n&#39;utilisent aucune nouvelle API introduite dans Flash Player 15.

   Si votre application Flash 14 doit utiliser une nouvelle API Flash 15, vous devez appeler dynamiquement l’API avec un cast vers le type Object, de sorte que l’application n’échoue pas dans Flash Player 14 au moment de l’exécution.

## Incrustations HTML {#html-overlays}

Dans Flash 15 et les versions ultérieures, vous pouvez gérer un affichage transparent des incrustations HTML lorsque le StageVideo matériel devient indisponible et revient au StageVideo logiciel. Pour activer cette fonction, définissez `wmode=opaque`.

Certains navigateurs plus anciens ne prennent pas en charge l’accélération matérielle. Pour plus d’informations sur ces exigences, voir Exigences [minimales](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md)StageVideo. Lorsque vous définissez `wmode=opaque`la vidéo, elle est rendue avec le logiciel StageVideo, ce qui peut avoir un impact sur les performances. En règle générale, la définition du rendu `wmode=direct` direct de la vidéo sur l’unité de traitement graphique améliore considérablement les performances. Cependant, cette option remplace également les incrustations HTML.
