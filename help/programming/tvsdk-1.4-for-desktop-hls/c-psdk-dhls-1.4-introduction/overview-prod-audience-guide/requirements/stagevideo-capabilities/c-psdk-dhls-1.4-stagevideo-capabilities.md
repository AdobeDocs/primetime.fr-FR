---
description: Sur les appareils qui prennent en charge l’accélération GPU (matériel), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo sur le matériel de l’appareil. La disponibilité de StageVideo dépend des versions et des fonctionnalités de différentes parties de votre système, y compris le Flash Player, le matériel vidéo, le système d’exploitation, les pilotes, le navigateur, la connexion réseau et le contexte d’affichage.
title: Fonctionnalités et restrictions de StageVideo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Présentation {#stagevideo-capabilities-and-restrictions-overview}

Sur les appareils qui prennent en charge l’accélération GPU (matériel), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo sur le matériel de l’appareil. La disponibilité de StageVideo dépend des versions et des fonctionnalités de différentes parties de votre système, y compris le Flash Player, le matériel vidéo, le système d’exploitation, les pilotes, le navigateur, la connexion réseau et le contexte d’affichage.

La variable `StageVideo` vous permet de tirer parti de l’accélération matérielle pour présenter la vidéo au niveau de performance le plus élevé possible pour un appareil. Disponibilité et performance de `StageVideo` est affecté par les facteurs suivants :

* **Accélération matérielle** - Lorsque l’accélération matérielle est disponible, `StageVideo` traite la vidéo sur le matériel de l’appareil. Lorsque l’accélération matérielle n’est pas disponible, la variable `StageVideo` les réponses dépendent de la version de Flash que vous exécutez :

   * *Flash 15 et versions ultérieures* - Lorsque l’accélération matérielle n’est pas disponible, `StageVideo` revient au logiciel, et vous n&#39;avez rien à faire.

     >[!TIP]
     >
     >Lorsque l’accélération matérielle n’est pas disponible, les performances peuvent considérablement diminuer.

   * *Flash 14 et versions antérieures* - Lorsque l’accélération matérielle n’est pas disponible, `StageVideo` devient indisponible. Dans un petit ensemble de configurations où l’accélération matérielle n’est pas prise en charge par le navigateur ou le processeur graphique, ou est désactivée dans le Flash Player, l’affichage vidéo avec la pile HLS TVSDK échoue. Dans le *HDS* pipeline, vous pouvez passer d’ `StageVideo` à un autre, tel que l’objet Vidéo, qui traite la vidéo dans le processeur.

* **Contexte de présentation** - Lors de l’affichage en plein écran `StageVideo` est toujours disponible et les performances seront au niveau maximum disponible sur l’appareil. Lorsque vous ne visualisez pas le mode Plein écran, la présentation vidéo est classée dans le contexte du navigateur, où sont utilisés les paramètres et fonctionnalités du navigateur.

* **wmode** - Dans le contexte du navigateur, la variable `wmode` est essentiel pour les performances. Adobe recommande de conserver `wmode` défini sur `direct` pour garantir les meilleures performances possibles dans le contexte du navigateur.

  >[!NOTE]
  >
  >Combinaison de facteurs qui incluent `wmode`, `StageVideo`, et le Flash génèrent des fonctionnalités et des restrictions différentes, selon la vitesse d’exécution de votre matériel et la version de Flash que vous utilisez.

   * *Flash 15 et versions ultérieures* - `StageVideo` est disponible avec tous les `wmode` paramètres. Cependant, si vous définissez `wmode` à un paramètre autre que `direct`, les performances seront plus faibles.

   * *Flash 14 et versions antérieures* - Si vous définissez `wmode` à un paramètre autre que `direct`, `StageVideo` n’est pas disponible dans tous les navigateurs.
