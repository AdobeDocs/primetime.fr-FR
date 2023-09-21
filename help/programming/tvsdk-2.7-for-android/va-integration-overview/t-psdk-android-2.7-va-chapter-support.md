---
title: Mise en oeuvre de la prise en charge des chapitres
description: Mise en oeuvre de la prise en charge des chapitres
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# Mise en oeuvre de la prise en charge des chapitres {#implement-chapter-support}

Vous pouvez définir et suivre *custom* chapitres pour le suivi vidéo dans les applications TVSDK.

Les chapitres personnalisés sont gérés par l’application et reposent sur des données CMS ou sur une autre manière dont l’application utilise pour définir des chapitres.

>[!CAUTION]
>
>Les chapitres par défaut ne sont pas pris en charge dans le TVSDK Android 2.5.

1. Définition et suivi de chapitres personnalisés.

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
