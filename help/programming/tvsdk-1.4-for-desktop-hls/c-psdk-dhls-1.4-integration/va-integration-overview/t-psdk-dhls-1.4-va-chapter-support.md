---
description: 'null'
seo-description: 'null'
seo-title: Mise en oeuvre de la prise en charge des chapitres
title: Mise en oeuvre de la prise en charge des chapitres
uuid: 85d14b83-7910-4f5d-9ef2-511de916abd6
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Mise en oeuvre de la prise en charge des chapitres {#implement-chapter-support}

Vous pouvez définir et suivre des chapitres pour le suivi vidéo dans une application basée sur TVSDK de différentes manières :

* Les chapitres par défaut sont gérés en interne par TVSDK.

   Un chapitre est défini comme l’intervalle entre chaque coupure publicitaire. Par exemple, le temps entre une coupure publicitaire preroll et la première coupure publicitaire mid-roll est défini comme le premier chapitre.
* Les chapitres personnalisés, qui sont gérés par l’application et reposent sur des données CMS ou sur une autre méthode utilisée par l’application pour définir des chapitres.

   Définissez et suivez les chapitres par défaut ou personnalisés.

   ```
   // First, enable chapter tracking by setting the boolean 'enableChapterTracking' to true: 
   
       vaMetadata.enableChapterTracking = true; 
   
   // For custom chapter definitions, provide an array of chapters through the metadata:  
   // For example: 3 chapters of 60 second duration each 
   
       var chapters:Vector.<VideoAnalyticsChapterData> = new Vector.<VideoAnalyticsChapterData>(); 
       var chapterDuration:int = 60; 
       for (var i:int = 0; i < 3; i++) { 
           var chapterData:VideoAnalyticsChapterData =  
             new VideoAnalyticsChapterData(i * chapterDuration, (i + 1) * chapterDuration); 
           chapterData.name = "chapter_%d" + (i+1); 
   
           chapters.push(chapterData); 
       } 
   
       vaMetadata.chapters = chapters; 
   
   // For default chapters, the application must not set custom chapters on the tracking metadata  
   // and simply enable chapters to be tracked by setting the boolean value as defined above. 
   ```

