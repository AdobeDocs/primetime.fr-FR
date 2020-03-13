---
description: Lorsque la lecture atteint une coupure publicitaire, franchit une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.
seo-description: Lorsque la lecture atteint une coupure publicitaire, franchit une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.
seo-title: Personnalisation de la lecture avec des publicités
title: Personnalisation de la lecture avec des publicités
uuid: 9cbf0bcf-7932-409e-a690-e79f284eaf74
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Présentation {#customize-playback-with-ads-overview}

Lorsque la lecture atteint une coupure publicitaire, franchit une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.

>[!TIP]
>
>Vous pouvez remplacer le comportement par défaut en utilisant la `AdBreakPolicySelector` classe.

Le comportement par défaut varie selon que l’utilisateur franchit la coupure publicitaire lors de la lecture normale ou en effectuant une recherche dans une vidéo ou en la repositionnant avec une avance rapide ou un retour arrière (lecture de l’astuce).

Vous pouvez personnaliser le comportement de lecture des publicités de différentes manières :

* Enregistrez la position où l’utilisateur a arrêté de regarder la vidéo et recommencez la lecture à la même position lors d’une session ultérieure.
* Si une coupure publicitaire est présentée à l’utilisateur, n’affichez aucune publicité supplémentaire pendant un certain nombre de minutes, même si l’utilisateur cherche une nouvelle position.
* Si la lecture du contenu échoue au bout de quelques minutes, redémarrez le flux ou passez à une autre source pour le même contenu.

   Lors de la session de lecture sur le basculement, pour permettre à l’utilisateur de sauter des publicités et de reprendre la position d’échec précédente, vous pouvez désactiver les publicités preroll et/ou mid-roll. TVSDK fournit des méthodes permettant d’ignorer les publicités preroll et mid-roll.