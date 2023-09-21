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

   ```js
   vaObj.videoMetadataBlock = function() { 
       return { 
           "name" : "my-video", 
           "genre" : "comedy" 
       }; 
   } 
   
   vaObj.adMetadataBlock = function(ad) { 
       return { 
           "name" : "my-ad", 
           "category" : "automotive" 
       }; 
   } 
   
   vaObj.chapterMetadataBlock = function(chapter) { 
       return { 
           "name" : "my-chapter", 
           "type" : "quartile" 
       }; 
   }
   ```
