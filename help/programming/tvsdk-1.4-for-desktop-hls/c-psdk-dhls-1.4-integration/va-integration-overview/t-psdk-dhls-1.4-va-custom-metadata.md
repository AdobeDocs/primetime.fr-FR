---
description: Vous pouvez fournir des métadonnées personnalisées sur le contenu, les publicités et les appels de suivi de chapitre à l’aide de fonctions de rappel.
title: Mise en oeuvre de la prise en charge des métadonnées personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# Mise en oeuvre de la prise en charge des métadonnées personnalisées{#implement-custom-metadata-support}

Vous pouvez fournir des métadonnées personnalisées sur le contenu, les publicités et les appels de suivi de chapitre à l’aide de fonctions de rappel.

Les fonctions de rappel sont invoquées juste avant l’appel de suivi. Votre application peut donc joindre les métadonnées spécifiques à une publicité ou à un chapitre.

1. Appeler des fonctions de rappel pour le contenu, les publicités et les chapitres.

   ```
   // Video Metadata Block 
   vaMetadata.videoMetadataBlock = function():Object { 
       return {"myvideoid":"1234", "mysdkversion":Version.version} 
   }; 
   
   // Ad Metadata Block invoked on every ad start 
   vaMetadata.adMetadataBlock = function(ad:Ad):Object { 
       return {"myadid":"ad-1234", "myad-sdkversion":Version.version} 
   }; 
   
   // Chapter Metadata Block invoked on every chapter start 
   vaMetadata.chapterMetadataBlock = function(chapter:VideoAnalyticsChapterData) { 
       return {"mychapterid":"chapter-1234", "mychapter-sdkversion":Version.version} 
   };
   ```
