---
description: 'null'
seo-description: 'null'
seo-title: Mise en oeuvre de la prise en charge des chapitres
title: Mise en oeuvre de la prise en charge des chapitres
uuid: 5b39e494-85ad-43bb-ab56-a55797aa4ef7
translation-type: tm+mt
source-git-commit: ''

---


# Mise en oeuvre de la prise en charge des chapitres {#implement-chapter-support}

Vous pouvez définir et suivre des chapitres pour le suivi vidéo dans une application basée sur TVSDK de différentes manières :

* Les chapitres par défaut sont gérés en interne par TVSDK.

   Un chapitre est défini comme l’intervalle entre chaque coupure publicitaire. Par exemple, le temps entre une coupure publicitaire preroll et la première coupure publicitaire mid-roll est défini comme le premier chapitre.
* Les chapitres personnalisés, qui sont gérés par l’application et sont basés sur les données CMS ou sur une autre méthode utilisée par l’application pour définir des chapitres.

1. Définissez et suivez les chapitres par défaut ou personnalisés.

   ```java
   // First, enable chapter tracking by setting  
   // the Boolean 'enableChapterTracking' to true: 
   
   vaMetadata.enableChapterTracking(true); 
   // For custom chapter definitions, provide an array list of chapters  
   // through the metadata. 
   // For example: 3 chapters of 60 second duration each 
   
   List<VideoAnalyticsChapterData> chapters = new ArrayList<VideoAnalyticsChapterData>(); 
   
   Int chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       VideoAnalyticsChapterData chapterData =  
         new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration);  
       chapterData.setName("chapter_" + (i+1)); 
       chapters.add(chapterData); 
   } 
   
   vaMetadata.setChapters(chapters); 
   // For default chapters, the application must not set  
   // custom chapters on the tracking metadata 
   // and simply enable chapters to be tracked by setting  
   // the boolean value as defined above.
   ```
