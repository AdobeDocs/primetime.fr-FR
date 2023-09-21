---
title: Insertion partielle d’une coupure publicitaire
description: Insertion partielle d’une coupure publicitaire
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Insertion d’une coupure publicitaire partielle {#partial-ad-break-insertion}

Vous pouvez activer une expérience de type télévision pour pouvoir rejoindre au milieu d’une publicité, dans des diffusions en direct. La fonction de coupure publicitaire partielle vous permet d’imiter une expérience de type télévision où, si le client lance une diffusion en direct dans un milieu, elle démarre dans ce milieu. Cela revient à passer à une chaîne de télévision et les publicités s&#39;exécutent en toute transparence.

Par exemple, si un utilisateur se joint au milieu d’une coupure publicitaire de 90 secondes (trois publicités de 30 secondes), 10 secondes après la seconde publicité (c’est-à-dire à 40 secondes de la coupure publicitaire), ce qui suit se produit :

* La seconde publicité est lue pendant la durée restante (20 secondes) suivie de la troisième publicité.
* Les dispositifs de suivi publicitaires pour la publicité partiellement lue (la deuxième publicité) ne sont pas déclenchés. Seul le dispositif de suivi de la troisième publicité est déclenché.

Ce comportement n’est pas activé par défaut. Pour activer cette fonctionnalité dans votre application, procédez comme suit :

Activez la préférence pour l’insertion de coupure publicitaire partielle. Utilisation de la nouvelle méthode `setPartialAdBreakPref` dans l’interface de MediaPlayer pour activer cette fonctionnalité. Utilisation `getPartialAdBreakPref` pour trouver l’état actuel de cette préférence.

```
    MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext()); 
    mediaPlayer.setPartialAdBreakPref(true);
```

La publicité preroll, si elle est disponible, est lue, puis le contenu est lu à partir du point d’exécution qui imite l’expérience de la télévision en direct.
