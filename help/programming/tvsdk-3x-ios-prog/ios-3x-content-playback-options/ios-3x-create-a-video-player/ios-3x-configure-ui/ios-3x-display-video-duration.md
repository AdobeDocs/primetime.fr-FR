---
description: Vous pouvez afficher la durée du contenu actuellement principal.
title: Afficher la durée de la vidéo
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---


# Affiche la durée de la vidéo {#display-the-duration-of-the-video}

Vous pouvez afficher la durée du contenu actuellement principal.

Mettez en oeuvre un affichage de durée de la vidéo à l’aide de l’exemple de code suivant :

    La propriété &quot;PTMediaPlayer&quot;, ` [seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange)&quot;, contient la plage de fenêtres pouvant être recherchée :
    
    * Pour VOD, cette plage correspond à la plage de contenu VOD complète, y compris les publicités.
    * Pour les variables en direct/linéaire, cette plage représente la fenêtre pouvant être recherchée.
    
    Pour plus d’informations sur l’API, voir [Référence de l’API TVSDK 3.4 pour iOS](https://help.adobe.com/en_US/primetime/api/psdk/appledoc_v3/index.html).

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
