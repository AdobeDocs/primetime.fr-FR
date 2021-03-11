---
description: Lorsque la lecture atteint une coupure publicitaire, passe une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.
title: Personnalisation de la lecture avec des publicités
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Aperçu {#customize-playback-with-ads}

Lorsque la lecture atteint une coupure publicitaire, passe une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.

>[!TIP]
>
>Vous pouvez remplacer le comportement par défaut en utilisant la classe `AdBreakPolicySelector`.

Le comportement par défaut varie selon que l’utilisateur franchit la coupure publicitaire au cours de la lecture normale ou en effectuant une recherche dans une vidéo ou en la repositionnant avec une avance rapide ou un rembobinage (lecture de l’astuce).

Vous pouvez personnaliser le comportement de lecture des publicités de différentes manières :

* Enregistrez la position où l’utilisateur a arrêté de regarder la vidéo et recommencez la lecture à la même position lors d’une session ultérieure.
* Si une coupure publicitaire est présentée à l’utilisateur, n’affichez aucune publicité supplémentaire pendant quelques minutes, même si l’utilisateur cherche à obtenir une nouvelle position.
* Si la lecture du contenu échoue après quelques minutes, redémarrez le flux ou passez à une autre source pour le même contenu.

   Lors de la session de lecture sur basculement, pour permettre à l’utilisateur de sauter des publicités et de revenir à la position d’échec précédente, vous pouvez désactiver les publicités preroll et/ou mid-roll. TVSDK fournit des méthodes permettant d’ignorer les publicités preroll et mid-roll.