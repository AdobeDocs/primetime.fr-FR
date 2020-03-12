---
description: A partir de Flash 15 et des versions ultérieures, lorsque le rendu matériel avec StageVideo n’est pas disponible, StageVideo revient sans problème à un objet StageVideo logiciel.
seo-description: A partir de Flash 15 et des versions ultérieures, lorsque le rendu matériel avec StageVideo n’est pas disponible, StageVideo revient sans problème à un objet StageVideo logiciel.
seo-title: Prise en charge de Flash 15 pour StageVideo
title: Prise en charge de Flash 15 pour StageVideo
uuid: 49bd8703-016e-4fda-8773-5254d4774ec6
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Prise en charge de Flash 15 pour StageVideo{#flash-support-for-stagevideo}

A partir de Flash 15 et des versions ultérieures, lorsque le rendu matériel avec StageVideo n’est pas disponible, StageVideo revient sans problème à un objet StageVideo logiciel.

Tenez compte des informations suivantes sur la reprise de Flash 15 StageVideo vers le logiciel :

* Aucune modification du code n’est requise dans votre application.
* Aucune modification n’est requise pour TVSDK.

   Vous n’avez pas besoin d’une mise à jour du SDK TVSDK pour utiliser la méthode de secours StageVideo dans le logiciel.
* Vos applications doivent être recompilées pour Flash 15.
* Les applications que vous recompilez pour Flash 15 continueront à fonctionner avec Flash 14 et les versions antérieures, à condition que ces applications n’utilisent aucune nouvelle API introduite dans Flash Player 15.

   Si votre application Flash 14 doit utiliser une nouvelle API Flash 15, vous devez appeler l’API de manière dynamique avec une conversion vers le type d’objet, de sorte que l’application n’échoue pas dans Flash Player 14 au moment de l’exécution.

## Incrustations HTML {#html-overlays}

Dans Flash 15 et les versions ultérieures, vous pouvez gérer un affichage transparent des incrustations HTML lorsque le matériel StageVideo devient indisponible et revient au logiciel StageVideo. Pour activer cette fonctionnalité, définissez `wmode=opaque`.

Certains anciens navigateurs ne prennent pas en charge l’accélération matérielle. Pour plus d’informations sur ces exigences, voir Configuration minimale requise [pour](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md)StageVideo. Lorsque vous définissez `wmode=opaque`la vidéo, elle est générée avec le logiciel StageVideo, ce qui peut avoir un impact sur les performances. En règle générale, la définition du rendu `wmode=direct` direct de la vidéo sur le GPU améliore considérablement les performances. Toutefois, cette option remplace également les incrustations HTML.
