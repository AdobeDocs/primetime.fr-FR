---
title: Insertion partielle d’une coupure publicitaire
description: Insertion partielle d’une coupure publicitaire
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Insertion partielle de coupure publicitaire {#partial-ad-break-insertion}

Vous pouvez activer une expérience TV de la possibilité de rejoindre au milieu d’une publicité, dans des flux en direct. La fonction de coupure publicitaire partielle vous permet d’imiter une expérience TV où, si le client début un flux en direct dans un milieu, il début dans ce milieu. Il est similaire à passer à un canal de télévision et les publicités fonctionnent sans accroc.

Par exemple, si un utilisateur se joint au milieu d’une coupure publicitaire de 90 secondes (trois publicités de 30 secondes), 10 secondes après la seconde publicité (c’est-à-dire à 40 secondes de la coupure publicitaire), ce qui suit se produit :

* La seconde publicité est lue pour la durée restante (20 s) suivie de la troisième publicité.
* Les suivis publicitaires pour la publicité partiellement lue (la deuxième publicité) ne sont pas déclenchés. Seul le suivi de la troisième publicité est déclenché.

Ce comportement n’est pas activé par défaut. Pour activer cette fonctionnalité dans votre application, procédez comme suit :

Activez la préférence pour l’insertion partielle de coupures publicitaires. Utilisez la nouvelle méthode `setPartialAdBreakPref` dans l’interface de MediaPlayer pour activer cette fonction. Utilisez la méthode `getPartialAdBreakPref` pour trouver l&#39;état actuel de cette préférence.

```
    MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext()); 
    mediaPlayer.setPartialAdBreakPref(true);
```

La publicité preroll, si elle est disponible, est lue, puis le contenu est lu à partir du point de lecture imitant l’expérience de la télévision en direct.
