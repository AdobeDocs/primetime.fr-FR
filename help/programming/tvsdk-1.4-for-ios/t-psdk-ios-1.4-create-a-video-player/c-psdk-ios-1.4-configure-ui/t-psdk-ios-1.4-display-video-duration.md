---
description: Vous pouvez afficher la durée du contenu actif.
seo-description: Vous pouvez afficher la durée du contenu actif.
seo-title: Afficher la durée de la vidéo
title: Afficher la durée de la vidéo
uuid: 02042070-9c55-4cbb-9dc1-49987451eb8f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Afficher la durée de la vidéo {#display-the-duration-of-the-video}

Vous pouvez afficher la durée du contenu actif.

Mettez en oeuvre un affichage de durée de la vidéo à l’aide de l’exemple de code suivant :

    La propriété &quot;PTMediaPlayer&quot;, [seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange), contient la plage de fenêtres pouvant être recherchée:
    
    * Pour VOD, cette plage est la plage de contenu VOD complète, y compris les publicités.
    * Dans le cas d’une version linéaire/en direct, cette plage représente la fenêtre pouvant être recherchée.
    
    Pour plus d’informations sur l’API, voir [Référence de l’API TVSDK 1.4 pour iOS](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/index.html)

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
