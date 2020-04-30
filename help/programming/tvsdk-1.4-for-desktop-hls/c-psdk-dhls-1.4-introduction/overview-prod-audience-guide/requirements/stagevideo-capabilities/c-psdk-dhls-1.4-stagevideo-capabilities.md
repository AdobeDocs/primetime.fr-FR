---
description: Sur les périphériques qui prennent en charge l’accélération GPU (matérielle), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo sur le matériel du périphérique. La disponibilité de StageVideo dépend des versions et des fonctionnalités de différentes parties de votre système, notamment Flash Player, le matériel vidéo, le système d’exploitation, les pilotes, le navigateur, la connexion réseau et le contexte d’affichage.
seo-description: Sur les périphériques qui prennent en charge l’accélération GPU (matérielle), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo sur le matériel du périphérique. La disponibilité de StageVideo dépend des versions et des fonctionnalités de différentes parties de votre système, notamment Flash Player, le matériel vidéo, le système d’exploitation, les pilotes, le navigateur, la connexion réseau et le contexte d’affichage.
seo-title: Fonctionnalités et restrictions de StageVideo
title: Fonctionnalités et restrictions de StageVideo
uuid: 7556f30b-4b9f-4258-beb6-2a4ce8f05d1a
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Présentation {#stagevideo-capabilities-and-restrictions-overview}

Sur les périphériques qui prennent en charge l’accélération GPU (matérielle), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo sur le matériel du périphérique. La disponibilité de StageVideo dépend des versions et des fonctionnalités de différentes parties de votre système, notamment Flash Player, le matériel vidéo, le système d’exploitation, les pilotes, le navigateur, la connexion réseau et le contexte d’affichage.

La `StageVideo` classe vous permet de tirer parti de l&#39;accélération matérielle pour présenter la vidéo au niveau de performance le plus élevé possible pour un périphérique. La disponibilité et le rendement de `StageVideo` l&#39;entreprise sont affectés par les facteurs suivants :

* **Accélération** matérielle - Lorsque l&#39;accélération matérielle est disponible, `StageVideo` traite la vidéo sur le matériel du périphérique. Lorsque l&#39;accélération matérielle n&#39;est pas disponible, les `StageVideo` réponses dépendent de la version de Flash que vous exécutez :

   * *Flash 15 et versions ultérieures* - Lorsque l&#39;accélération matérielle n&#39;est pas disponible, `StageVideo` revient au logiciel et vous n&#39;avez rien à faire.

      >[!TIP]
      >
      >Lorsque l&#39;accélération matérielle n&#39;est pas disponible, les performances peuvent se dégrader considérablement.

   * *Flash 14 et versions antérieures* - Lorsque l&#39;accélération matérielle n&#39;est pas disponible, `StageVideo` elle devient indisponible. Dans un petit ensemble de configurations où l&#39;accélération matérielle n&#39;est pas prise en charge par le navigateur ou le GPU, ou est désactivée dans Flash Player, l&#39;affichage vidéo avec la pile TVSDK HLS échoue. Dans le pipeline *HDS* , vous pouvez passer `StageVideo` à un autre, tel que l’objet Video, qui traite la vidéo dans le processeur.

* **Contexte** de la présentation - Lors de l&#39;affichage en plein écran, `StageVideo` est toujours disponible et les performances seront au niveau maximum disponible sur l&#39;appareil. Lorsque vous ne visualisez pas la vidéo en plein écran, la présentation vidéo est placée dans le contexte du navigateur, où sont utilisés les paramètres et les fonctionnalités du navigateur.

* **wmode** - Dans le contexte du navigateur, le `wmode` paramètre est essentiel aux performances. Adobe recommande de rester `wmode` configuré pour `direct` garantir les meilleures performances possibles dans le contexte du navigateur.

   >[!NOTE]
   >
   >La combinaison de facteurs incluant `wmode`, `StageVideo`et Flash entraîne différentes fonctionnalités et restrictions, selon la vitesse d&#39;exécution de votre matériel et la version de Flash que vous utilisez.

   * *Flash 15 et versions ultérieures* - `StageVideo` est disponible avec tous les paramètres `wmode` disponibles. Cependant, si vous définissez `wmode` un paramètre autre que `direct`, les performances seront inférieures.

   * *Flash 14 et versions antérieures* - Si vous définissez `wmode` un paramètre autre que `direct`, `StageVideo` il n’est pas disponible dans tous les navigateurs.

