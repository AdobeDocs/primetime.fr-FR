---
description: 'null'
seo-description: 'null'
seo-title: Insertion partielle d’une coupure publicitaire
title: Insertion partielle d’une coupure publicitaire
uuid: cc071c89-f813-419e-a2b2-4f6a9fdccd6a
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Insertion partielle d’une coupure publicitaire {#partial-ad-break-insertion}

Vous pouvez activer une expérience TV de la possibilité de rejoindre au milieu d’une publicité, dans des flux en direct. La fonction de coupure publicitaire partielle vous permet d’imiter une expérience TV où, si le client début un flux en direct dans un milieu, il début dans ce milieu. Il est similaire à passer à un canal de télévision et les publicités fonctionnent sans accroc.

Par exemple, si un utilisateur se joint au milieu d’une coupure publicitaire de 90 secondes (trois publicités de 30 secondes), 10 secondes après la seconde publicité (c’est-à-dire à 40 secondes de la coupure publicitaire), ce qui suit se produit :

* La seconde publicité est lue pour la durée restante (20 s) suivie de la troisième publicité.
* Les suivis publicitaires pour la publicité partiellement lue (la deuxième publicité) ne sont pas déclenchés. Seul le suivi de la troisième publicité est déclenché.

Ce comportement n’est pas activé par défaut. Pour activer cette fonctionnalité dans votre application, procédez comme suit :

1. Désactivez les droits en direct, à l’aide de la méthode setEnableLivePreroll de la classe AdvertisingMetadata.

   ```
   advertisingMetadata.setLivePreroll(false)  
   advertisingMetadata.setPreroll(false)
   ```

1. Activez la préférence pour l’insertion partielle de coupures publicitaires. Utilisez la nouvelle méthode setPartialAdBreakPref dans l’interface MediaPlayer pour activer cette fonction. Utilisez la méthode getPartialAdBreakPref pour trouver l’état actuel de cette préférence.

   ```
   MediaPlayer mediaPlayer = new MediaPlayer(getActivity().getApplicationContext()); 
    mediaPlayer.setPartialAdBreakPref(true);
   ```

