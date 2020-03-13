---
description: 'null'
seo-description: 'null'
seo-title: Mise en oeuvre de la prise en charge des chapitres
title: Mise en oeuvre de la prise en charge des chapitres
uuid: 6e2c3994-d28b-489f-ae60-9b876125a871
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Mise en oeuvre de la prise en charge des chapitres {#implement-chapter-support}

Vous pouvez définir et suivre des chapitres *personnalisés* pour le suivi vidéo dans les applications basées sur TVSDK.

Les chapitres personnalisés sont gérés par l’application et reposent sur des données CMS ou sur une autre méthode utilisée par l’application pour définir des chapitres.

>[!CAUTION]
>
>Les chapitres par défaut ne sont pas pris en charge dans le kit TVSDK Android 3.0.

Définissez et suivez les chapitres personnalisés.

```java
// First, enable chapter tracking by setting   
// enableChapterTracking to true: 
 
vaMetadata.enableChapterTracking(true); 
// For custom chapter definitions, provide  
// an array list of chapters through the metadata. 
// For example: 3 chapters of 60 second duration each 
 
List<VideoAnalyticsChapterData> chapters =  
  new ArrayList<VideoAnalyticsChapterData>(); 
 
Int chapterDuration = 60; 
for (var i = 0; i < 3; i++) { 
    VideoAnalyticsChapterData chapterData =  
      new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration);  
    chapterData.setName("chapter_" + (i+1)); 
    chapters.add(chapterData); 
} 
 
vaMetadata.setChapters(chapters); 
```
