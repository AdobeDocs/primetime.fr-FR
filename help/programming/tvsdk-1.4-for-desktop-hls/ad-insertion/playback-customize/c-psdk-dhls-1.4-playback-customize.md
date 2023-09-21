---
description: Lorsque la lecture atteint une coupure publicitaire, transmet une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.
title: Personnalisation de la lecture avec des publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Présentation {#customize-playback-with-ads-overview}

Lorsque la lecture atteint une coupure publicitaire, transmet une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.

>[!TIP]
>
>Vous pouvez remplacer le comportement par défaut en utilisant la variable `AdPolicySelector` classe .

Le comportement par défaut varie, selon que l’utilisateur passe la coupure publicitaire lors de la lecture normale ou en effectuant une recherche dans une vidéo ou en la repositionnant avec une progression rapide ou un retour arrière (lecture de l’astuce).

Vous pouvez personnaliser le comportement de lecture des publicités comme suit :

* Enregistrez la position où l’utilisateur a cessé de regarder la vidéo et a repris la lecture à la même position lors d’une session ultérieure.
* Si une coupure publicitaire est présentée à l’utilisateur, n’affiche aucune publicité supplémentaire pendant un certain nombre de minutes, même si l’utilisateur recherche une nouvelle position.
* Si la lecture du contenu échoue au bout de quelques minutes, redémarrez le flux ou passez à une autre source pour le même contenu.

  Lors de la session de lecture sur le basculement, pour permettre à l’utilisateur d’ignorer les publicités et de reprendre la position d’échec précédente, vous pouvez désactiver les publicités preroll et/ou mid-roll. TVSDK fournit des méthodes pour activer le saut des publicités preroll et mid-roll.
