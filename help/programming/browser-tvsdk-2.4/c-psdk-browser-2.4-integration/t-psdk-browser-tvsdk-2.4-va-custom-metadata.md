---
description: Vous pouvez fournir des métadonnées personnalisées sur le contenu, les publicités et les appels de suivi de chapitre en utilisant les fonctions de rappel.
seo-description: Vous pouvez fournir des métadonnées personnalisées sur le contenu, les publicités et les appels de suivi de chapitre en utilisant les fonctions de rappel.
seo-title: Mise en oeuvre de la prise en charge des métadonnées personnalisées
title: Mise en oeuvre de la prise en charge des métadonnées personnalisées
uuid: 6e23311c-a393-4485-919e-4cf6412789b1
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Mise en oeuvre de la prise en charge des métadonnées personnalisées{#implement-custom-metadata-support}

Vous pouvez fournir des métadonnées personnalisées sur le contenu, les publicités et les appels de suivi de chapitre en utilisant les fonctions de rappel.

Les fonctions de rappel sont invoquées juste avant l’appel de suivi, de sorte que votre application peut joindre les métadonnées spécifiques à une publicité ou à un chapitre.

1. Appelez des fonctions de rappel pour le contenu, les publicités et les chapitres.

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

