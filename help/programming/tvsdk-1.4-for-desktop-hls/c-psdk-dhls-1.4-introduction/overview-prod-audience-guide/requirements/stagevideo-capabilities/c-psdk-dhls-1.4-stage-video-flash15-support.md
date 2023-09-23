---
description: À partir du Flash 15 et de la version ultérieure, lorsque le rendu matériel avec StageVideo n’est pas disponible, StageVideo revient facilement à un objet StageVideo logiciel.
title: Prise en charge de Flash 15 pour StageVideo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Prise en charge de Flash 15 pour StageVideo{#flash-support-for-stagevideo}

À partir du Flash 15 et de la version ultérieure, lorsque le rendu matériel avec StageVideo n’est pas disponible, StageVideo revient facilement à un objet StageVideo logiciel.

Tenez compte des informations suivantes sur le Flash 15 de la version de secours de StageVideo en logiciels :

* Aucune modification du code n’est requise dans votre application.
* Aucune modification apportée à TVSDK n’est requise.

  Vous n’avez pas besoin d’une mise à jour de TVSDK pour utiliser la solution de secours StageVideo dans le logiciel.
* Vos applications doivent être recompilées pour le Flash 15.
* Les applications que vous recompilez pour le Flash 15 continueront à fonctionner avec le Flash 14 et les versions antérieures, à condition que ces applications n’utilisent aucune nouvelle API introduite dans le Flash Player 15.

  Si votre application Flash 14 doit utiliser une nouvelle API Flash 15, vous devez appeler dynamiquement l’API avec une conversion vers le type Objet, de sorte que l’application n’échoue pas dans le Flash Player 14 au moment de l’exécution.

## Superpositions de HTMLs {#html-overlays}

Dans Flash 15 et versions ultérieures, vous pouvez conserver un affichage transparent des recouvrements de HTML lorsque le composant StageVideo matériel devient indisponible et revient au composant StageVideo logiciel. Pour activer cette fonction, définissez `wmode=opaque`.

Certains navigateurs plus anciens ne prennent pas en charge l’accélération matérielle. Pour plus d’informations sur ces exigences, voir [Exigences minimales de StageVideo](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md). Lorsque vous définissez `wmode=opaque`, la vidéo est rendue avec le logiciel StageVideo, ce qui peut avoir un impact sur les performances. En règle générale, la définition de `wmode=direct` effectue directement le rendu de la vidéo sur le processeur graphique, ce qui se traduit par de meilleures performances. Toutefois, cette option remplace également les incrustations de HTML.
