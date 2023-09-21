---
description: À l’aide de marqueurs d’annonce personnalisés, vous pouvez marquer des sections spécifiques du contenu principal en tant que périodes de contenu liées à la publicité.
title: Ajout de marqueurs de publicité personnalisés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Présentation {#add-custom-ad-markers-overview}

À l’aide de marqueurs d’annonce personnalisés, vous pouvez marquer des sections spécifiques du contenu principal en tant que périodes de contenu liées à la publicité.

Cette fonctionnalité est particulièrement utile lorsque le contenu est enregistré, par exemple, à partir d’un événement en direct, et que le résultat de l’enregistrement est un flux HLS. L’enregistrement contient le contenu principal et le contenu lié à la publicité dans un flux vidéo à la demande (VOD) HLS. Le processus d’enregistrement ne permet pas de suivre les segments liés aux publicités. Les informations relatives au positionnement des publicités dans le contenu principal sont donc perdues.

Vous pouvez obtenir les informations relatives au positionnement des périodes de contenu publicitaire à partir d’autres sources hors-bande, telles que les systèmes CMS externes. Vous pouvez définir des marqueurs personnalisés, par le biais desquels ces informations hors bande peuvent être transmises au sous-système du gestionnaire de chronologies. L’intention est de marquer les sections de contenu qui correspondent au contenu associé à la publicité spécifiée de sorte que tous les événements de lecture spécifiques à la publicité soient déclenchés de la même manière que si ces périodes publicitaires personnalisées ont été explicitement placées dans la chronologie du lecteur.

Le suivi des publicités n’est pas géré en interne par TVSDK, par exemple lorsque les publicités sont résolues par la prise de décision publicitaire Adobe Primetime. Toutefois, TVSDK fournit les abstractions suivantes qui définissent la manière dont le contenu lié aux publicités est représenté sur la chronologie :

* La coupure publicitaire

  Une coupure publicitaire est une liste ordonnée de publicités consécutives individuelles.
* Une publicité individuelle

Les événements de lecture sont déclenchés séparément pour les coupures publicitaires et les publicités aux points de début et de fin de chaque publicité.

TVSDK distribue des événements de suivi publicitaire à votre application, de sorte que vous puissiez mettre en oeuvre votre propre logique de suivi. Si vous définissez des marqueurs de publicité personnalisés, vous recevez le `onAdBreakStart`, `onAdStart`, `onAdProgress`, `onAdComplete`, et `onAdBreakComplete` événements .
