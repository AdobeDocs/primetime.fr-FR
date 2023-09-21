---
title: Mise en oeuvre de la prise en charge des chapitres
description: Mise en oeuvre de la prise en charge des chapitres
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%

---

# Mise en oeuvre de la prise en charge des chapitres{#implement-chapter-support}

Un chapitre est défini comme l’intervalle entre chaque coupure publicitaire. Par exemple, le temps entre une coupure publicitaire preroll et la première coupure publicitaire mid-roll est défini comme le premier chapitre. Vous pouvez définir et suivre des chapitres pour le suivi vidéo dans une application basée sur Browser TVSDK à l’aide de chapitres personnalisés. Les chapitres personnalisés sont gérés par l’application et sont basés sur des données CMS ou sur une autre manière dont l’application utilise pour définir des chapitres.

1. Définition et suivi de chapitres personnalisés.

   ```js
   vaObj.enableChapterTracking = true; 
   
   // For custom chapter definitions, provide an array of chapters through the metadata: 
   // For example: 3 chapters of 60 second duration each 
   var chapters = []; 
   var chapterDuration = 60; 
   for (var i = 0; i < 3; i++) { 
       var chapterData = new AdobePSDK.VA.VideoAnalyticsChapterData("chapter_" + (i+1), i * chapterDuration, chapterDuration, (i+1)); 
       chapters.push(chapterData); 
   } 
   
   vaObj.chapters = chapters;
   ```
