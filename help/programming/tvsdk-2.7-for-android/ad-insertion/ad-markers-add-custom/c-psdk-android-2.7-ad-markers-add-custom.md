---
description: Grâce aux marqueurs publicitaires personnalisés, vous pouvez marquer des sections spécifiques du contenu principal comme des périodes de contenu liées aux publicités.
seo-description: Grâce aux marqueurs publicitaires personnalisés, vous pouvez marquer des sections spécifiques du contenu principal comme des périodes de contenu liées aux publicités.
seo-title: Ajouter de marqueurs publicitaires personnalisés
title: Ajouter de marqueurs publicitaires personnalisés
uuid: 712da406-094a-49b2-b21d-4d5d73fff8cf
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#add-custom-ad-markers-overview}

Grâce aux marqueurs publicitaires personnalisés, vous pouvez marquer des sections spécifiques du contenu principal comme des périodes de contenu liées aux publicités.

Cette fonctionnalité est particulièrement utile lorsque du contenu est enregistré, par exemple, à partir d’un  en direct, et que le résultat de l’enregistrement est un flux HLS. L’enregistrement contient le contenu principal et le contenu publicitaire dans un flux vidéo à la demande (VOD) HLS. Le processus d’enregistrement ne suit pas les segments liés aux publicités. Les informations liées au positionnement des publicités dans le contenu principal sont donc perdues.

Vous pouvez obtenir les informations liées au positionnement des périodes de contenu publicitaire à partir d’autres sources hors bande, telles que des systèmes CMS externes. Vous pouvez définir des marqueurs personnalisés grâce auxquels ces informations hors bande peuvent être transmises au sous-système du gestionnaire de chronologie. L’intention est de marquer les sections de contenu qui correspondent au contenu de la publicité spécifiée de telle sorte que tous les  de lecture spécifiques à la publicité soient déclenchés de la même manière que si ces périodes publicitaires personnalisées étaient explicitement placées sur la chronologie du lecteur.

Le suivi des publicités n’est pas géré en interne par TVSDK, par exemple lorsque les publicités sont résolues par la prise de décision publicitaire Adobe Primetime. Néanmoins, TVSDK fournit les abstractions suivantes qui définissent la manière dont le contenu associé aux publicités est représenté sur la chronologie :

* La coupure publicitaire

   Une coupure publicitaire est un  ordonné de publicités consécutives individuelles.
* Une publicité individuelle

Les  de lecture sont déclenchées séparément pour les coupures publicitaires et les publicités au  de la et au point de fin de chaque publicité.

TVSDK distribue des de suivi publicitaire  à votre application afin que vous puissiez mettre en oeuvre votre propre logique de suivi. Si vous définissez des marqueurs publicitaires personnalisés, vous recevez les  `onAdBreakStart`, `onAdStart`, `onAdProgress`, `onAdComplete`et `onAdBreakComplete` .