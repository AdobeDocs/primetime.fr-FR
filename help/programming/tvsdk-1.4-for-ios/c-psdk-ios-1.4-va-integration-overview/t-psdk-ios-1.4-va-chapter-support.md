---
title: Mise en oeuvre de la prise en charge des chapitres
description: Mise en oeuvre de la prise en charge des chapitres
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Mise en oeuvre de la prise en charge des chapitres{#implement-chapter-support}

Vous pouvez définir et effectuer le suivi des chapitres pour le suivi vidéo dans une application TVSDK en procédant comme suit :

* Les chapitres par défaut, gérés en interne par TVSDK.

  Un chapitre est défini comme l’intervalle entre chaque coupure publicitaire. Par exemple, le temps entre une coupure publicitaire preroll et la première coupure publicitaire mid-roll est défini comme le premier chapitre.
* Les chapitres personnalisés, qui sont gérés par l’application et sont basés sur des données CMS ou sur une autre manière dont l’application utilise pour définir des chapitres.

  Définissez et effectuez le suivi des chapitres par défaut ou personnalisés.

  ```
  // First, enable chapter tracking by setting the boolean 'enableChapterTracking' to true: 
  
      vaTrackingMetadata.enableChapterTracking = YES; 
  
  // For custom chapter definitions, provide an array of chapters through the metadata:  
  // For example, 3 chapters of 60 second duration each: 
  
      NSMutableArray *chapters = [[[NSMutableArray alloc] init] autorelease]; 
  
      int chapterDuration = 60; 
      for (int i = 0; i < 3; i++) 
      { 
          PTVideoAnalyticsChapterData *chapterData =  
            [[[PTVideoAnalyticsChapterData alloc] init] autorelease]; 
          chapterData.name = [NSString stringWithFormat:@"chapter_%d", (i+1)]; 
          chapterData.range =  
            CMTimeRangeMake(CMTimeMakeWithSeconds(i * chapterDuration, 10000),  
            CMTimeMakeWithSeconds(chapterDuration, 10000)); 
  
          [chapters addObject:chapterData]; 
      } 
  
      vaTrackingMetadata.chapters = chapters; 
  
  // For default chapters, the application must not set custom chapters on the tracking metadata  
  // and simply enable chapters to be tracked by setting the boolean value as defined above.
  ```
