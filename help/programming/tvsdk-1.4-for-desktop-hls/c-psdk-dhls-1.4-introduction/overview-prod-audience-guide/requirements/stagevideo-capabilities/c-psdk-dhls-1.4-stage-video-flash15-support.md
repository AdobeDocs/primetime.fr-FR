---
description: A partir du Flash 15 et des versions ultérieures, lorsque le rendu matériel avec StageVideo n’est pas disponible, StageVideo revient en douceur à un objet StageVideo logiciel.
title: Prise en charge du Flash 15 pour StageVideo
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---


# Prise en charge du Flash 15 pour StageVideo{#flash-support-for-stagevideo}

A partir du Flash 15 et des versions ultérieures, lorsque le rendu matériel avec StageVideo n’est pas disponible, StageVideo revient en douceur à un objet StageVideo logiciel.

Tenez compte des informations suivantes sur la reprise de Flash 15 StageVideo par rapport au logiciel :

* Aucune modification du code n’est requise dans votre application.
* Aucune modification apportée à TVSDK n’est requise.

   Vous n’avez pas besoin d’une mise à jour de TVSDK pour utiliser le logiciel de secours StageVideo.
* Vos applications doivent être recompilées pour le Flash 15.
* Les applications que vous recompilez pour le Flash 15 continueront à fonctionner avec le Flash 14 et les versions antérieures, à condition que ces applications n’utilisent aucune nouvelle API introduite dans le Flash Player 15.

   Si votre application Flash 14 doit utiliser une nouvelle API Flash 15, vous devez appeler dynamiquement l’API avec un cast vers le type Object, de sorte que l’application n’échoue pas dans le Flash Player 14 au moment de l’exécution.

## Incrustations HTML {#html-overlays}

Dans le Flash 15 et les versions ultérieures, vous pouvez gérer un affichage transparent des incrustations HTML lorsque le StageVideo matériel devient indisponible et revient au StageVideo logiciel. Pour activer cette fonctionnalité, définissez `wmode=opaque`.

Certains navigateurs plus anciens ne prennent pas en charge l’accélération matérielle. Pour plus d’informations sur ces exigences, voir [Exigences minimales de StageVideo](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md). Lorsque vous définissez `wmode=opaque`, la vidéo est rendue avec le logiciel StageVideo, ce qui peut avoir un impact sur les performances. En règle générale, la définition de `wmode=direct` rend directement la vidéo au processeur graphique, ce qui se traduit par de meilleures performances. Cependant, cette option remplace également les incrustations HTML.
