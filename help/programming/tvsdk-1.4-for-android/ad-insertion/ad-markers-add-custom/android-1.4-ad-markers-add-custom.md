---
description: En utilisant des marqueurs publicitaires personnalisés, vous pouvez marquer des sections spécifiques du contenu principal comme des périodes de contenu liées à la publicité.
seo-description: En utilisant des marqueurs publicitaires personnalisés, vous pouvez marquer des sections spécifiques du contenu principal comme des périodes de contenu liées à la publicité.
seo-title: Ajouter des marqueurs publicitaires personnalisés
title: Ajouter des marqueurs publicitaires personnalisés
uuid: 5d8c8aaa-a4e7-499d-b70e-5c72007ec269
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Aperçu {#add-custom-ad-markers-overview}

En utilisant des marqueurs publicitaires personnalisés, vous pouvez marquer des sections spécifiques du contenu principal comme des périodes de contenu liées à la publicité.

Cette fonction est particulièrement utile lorsque du contenu est enregistré, par exemple, à partir d’un événement actif et que le résultat de l’enregistrement est un flux HLS. L’enregistrement contient le contenu principal et le contenu lié à la publicité dans un flux vidéo à la demande (VOD) HLS. Le processus d’enregistrement ne suit pas les segments liés aux publicités, de sorte que les informations liées à la position des publicités dans le contenu principal sont perdues.

Vous pouvez obtenir les informations liées au positionnement des périodes de contenu publicitaire à partir d’autres sources hors bande, telles que les systèmes CMS externes. Vous pouvez définir des marqueurs personnalisés grâce auxquels ces informations hors bande peuvent être transmises au sous-système du gestionnaire de chronologie. L’intention est de marquer les sections de contenu qui correspondent au contenu publicitaire spécifié de telle sorte que tous les événements de lecture spécifiques à une publicité soient déclenchés de la même manière que si ces périodes publicitaires personnalisées étaient explicitement placées sur la chronologie du lecteur.

Le suivi des publicités n’est pas géré en interne par TVSDK, par exemple lorsque les publicités sont résolues par la prise de décision des publicités Adobe Primetime (précédemment connue sous le nom d’Auditude). Néanmoins, TVSDK fournit les abstractions suivantes qui définissent la manière dont le contenu associé à la publicité est représenté sur la chronologie :

* La coupure publicitaire

   Une coupure publicitaire est une liste ordonnée de publicités consécutives individuelles.
* Une publicité individuelle

Les événements de lecture sont déclenchés séparément pour les coupures publicitaires et les publicités aux points de début et de fin de chaque publicité.

TVSDK distribue des événements de suivi publicitaire à votre application afin que vous puissiez mettre en oeuvre votre propre logique de suivi. Si vous définissez des marqueurs publicitaires personnalisés, vous recevez les événements `onAdBreakStart`, `onAdStart`, `onAdProgress`, `onAdComplete` et `onAdBreakComplete`.
