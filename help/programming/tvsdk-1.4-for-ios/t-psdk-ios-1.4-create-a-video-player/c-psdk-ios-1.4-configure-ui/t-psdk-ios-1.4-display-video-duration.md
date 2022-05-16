---
description: Vous pouvez afficher la durée du contenu actuellement principal.
title: Afficher la durée de la vidéo
exl-id: 4e31d784-4d16-470b-8317-11be32a55c2f
source-git-commit: 0019a95fa9ca6d21249533d559ce844897ab67cf
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Afficher la durée de la vidéo {#display-the-duration-of-the-video}

Vous pouvez afficher la durée du contenu actuellement principal.

Implémentez un affichage de durée de la vidéo à l’aide de l’exemple de code suivant :

Le `PTMediaPlayer` property, [seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange), contient la plage de fenêtres sélectionnables actuelle :

* Pour VOD, cette plage correspond à l’ensemble de la plage de contenu VOD, y compris les publicités.
* Pour la ligne/linéaire, cette plage représente la fenêtre pouvant faire l’objet d’une recherche.

Pour plus d’informations sur l’API, voir [Référence de l’API TVSDK 1.4 pour iOS](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/index.html)

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
