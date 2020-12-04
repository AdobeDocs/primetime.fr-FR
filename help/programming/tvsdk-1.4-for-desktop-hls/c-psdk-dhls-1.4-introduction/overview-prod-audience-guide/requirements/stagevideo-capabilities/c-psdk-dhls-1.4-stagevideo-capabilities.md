---
description: Sur les périphériques qui prennent en charge l’accélération GPU (matérielle), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo sur le matériel du périphérique. La disponibilité de StageVideo dépend des versions et des fonctionnalités des différentes parties de votre système, notamment le Flash Player, le matériel vidéo, le système d’exploitation, les pilotes, le navigateur, la connexion réseau et le contexte d’affichage.
seo-description: Sur les périphériques qui prennent en charge l’accélération GPU (matérielle), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo sur le matériel du périphérique. La disponibilité de StageVideo dépend des versions et des fonctionnalités des différentes parties de votre système, notamment le Flash Player, le matériel vidéo, le système d’exploitation, les pilotes, le navigateur, la connexion réseau et le contexte d’affichage.
seo-title: Fonctionnalités et restrictions de StageVideo
title: Fonctionnalités et restrictions de StageVideo
uuid: 7556f30b-4b9f-4258-beb6-2a4ce8f05d1a
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Aperçu {#stagevideo-capabilities-and-restrictions-overview}

Sur les périphériques qui prennent en charge l’accélération GPU (matérielle), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo sur le matériel du périphérique. La disponibilité de StageVideo dépend des versions et des fonctionnalités des différentes parties de votre système, notamment le Flash Player, le matériel vidéo, le système d’exploitation, les pilotes, le navigateur, la connexion réseau et le contexte d’affichage.

La classe `StageVideo` vous permet de tirer parti de l&#39;accélération matérielle pour présenter la vidéo au niveau de performance le plus élevé possible pour un périphérique. La disponibilité et les performances de `StageVideo` sont affectées par les facteurs suivants :

* **Accélération**  matérielle - Lorsque l&#39;accélération matérielle est disponible,  `StageVideo` traite la vidéo sur le matériel du périphérique. Lorsque l&#39;accélération matérielle n&#39;est pas disponible, la réponse `StageVideo` dépend de la version du Flash en cours d&#39;exécution :

   * *Flash 15 et versions ultérieures*  - Lorsque l&#39;accélération matérielle n&#39;est pas disponible,  `StageVideo` retombe au logiciel, et vous n&#39;avez rien à faire.

      >[!TIP]
      >
      >Lorsque l&#39;accélération matérielle n&#39;est pas disponible, les performances peuvent se dégrader considérablement.

   * *Flash 14 et versions antérieures*  - Lorsque l&#39;accélération matérielle n&#39;est pas disponible,  `StageVideo` elle ne l&#39;est plus. Dans un petit ensemble de configurations où l&#39;accélération matérielle n&#39;est pas prise en charge par le navigateur ou le GPU, ou est désactivée dans le Flash Player, l&#39;affichage vidéo avec la pile TVSDK HLS échoue. Dans le pipeline *HDS*, vous pouvez passer de `StageVideo` à un autre, tel que l’objet Video, qui traite la vidéo dans le processeur.

* **Contexte**  de la présentation - Lors de l&#39;affichage en plein écran,  `StageVideo` est toujours disponible et les performances seront au niveau maximum disponible sur l&#39;appareil. Lorsque vous ne visualisez pas la vidéo en plein écran, la présentation vidéo est placée dans le contexte du navigateur, où sont utilisés les paramètres et les fonctionnalités du navigateur.

* **wmode**  - Dans le contexte du navigateur, le  `wmode` paramètre est essentiel aux performances. L’Adobe vous recommande de conserver `wmode` défini sur `direct` pour garantir les meilleures performances possibles dans le contexte du navigateur.

   >[!NOTE]
   >
   >La combinaison de facteurs incluant `wmode`, `StageVideo` et le Flash entraîne des capacités et des restrictions différentes, selon la vitesse d&#39;exécution de votre matériel et la version du Flash que vous utilisez.

   * *Flash 15 et versions ultérieures*  -  `StageVideo` est disponible avec tous les  `wmode` paramètres disponibles. Cependant, si vous définissez `wmode` sur un paramètre autre que `direct`, les performances seront inférieures.

   * *Flash 14 et versions antérieures*  - Si vous définissez  `wmode` un paramètre autre que  `direct`celui-ci,  `StageVideo` il n’est pas disponible dans tous les navigateurs.

