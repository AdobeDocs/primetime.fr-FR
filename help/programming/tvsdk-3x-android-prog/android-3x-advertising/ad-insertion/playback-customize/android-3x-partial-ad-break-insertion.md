---
description: 'null'
seo-description: 'null'
seo-title: Insertion partielle de saut de publicité
title: Insertion partielle de saut de publicité
uuid: a81295b8-77fe-4475-a472-080ee7804d7a
translation-type: tm+mt
source-git-commit: fe9d7d1b2b23a70eb4e212de3d9bda47fc11d8f1

---


# Insertion partielle de coupure publicitaire {#partial-ad-break-insertion}

Vous pouvez activer une expérience de type TV pour pouvoir rejoindre au milieu d’une publicité, dans des flux en direct. La fonction de coupure publicitaire partielle vous permet d’imiter une expérience de type TV où, si le client  un flux en direct à l’intérieur d’un milieu, il  dans ce milieu. C&#39;est similaire à passer à un de télévision et les publicités s&#39;exécutent sans problème.

Par exemple, si un utilisateur se joint au milieu d’une coupure publicitaire de 90 secondes (trois publicités de 30 secondes), de 10 secondes dans la seconde publicité (c’est-à-dire, à 40 secondes de la coupure publicitaire), ce qui suit se produit :

* La seconde publicité est lue pendant la durée restante (20 s), suivie de la troisième publicité.
* Les suivis publicitaires pour la publicité partiellement lue (la deuxième publicité) ne sont pas déclenchés. Seul le suivi de la troisième publicité est déclenché.

Ce comportement n’est pas activé par défaut. Pour activer cette fonctionnalité dans votre application, procédez comme suit :

Activez la préférence pour l’insertion partielle de coupures publicitaires. Utilisez la nouvelle méthode `setPartialAdBreakPref` dans l’interface de MediaPlayer pour activer cette fonction. Utilisez `getPartialAdBreakPref` la méthode pour trouver l’état actuel de cette préférence.

```
    MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext()); 
    mediaPlayer.setPartialAdBreakPref(true);
```

La publicité preroll, si elle est disponible, est lue, puis le contenu est lu à partir du point de diffusion qui imite l’expérience de la télévision en direct.
