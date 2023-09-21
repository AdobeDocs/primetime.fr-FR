---
description: Vous pouvez fournir des métadonnées personnalisées sur le contenu, les publicités et les appels de suivi de chapitre à l’aide de fonctions de rappel.
title: Mise en oeuvre de la prise en charge des métadonnées personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# Mise en oeuvre de la prise en charge des métadonnées personnalisées {#implement-custom-metadata-support}

Vous pouvez fournir des métadonnées personnalisées sur le contenu, les publicités et les appels de suivi de chapitre à l’aide de fonctions de rappel.

Les fonctions de rappel sont invoquées juste avant l’appel de suivi. Votre application peut donc joindre les métadonnées spécifiques à une publicité ou à un chapitre.

Appeler des fonctions de rappel pour le contenu, les publicités et les chapitres.

```java
// Video Metadata Block 
vaMetadata.setVideoMetadataBlock(new VideoAnalyticsMetadata.VideoMetadataBlock() { 
    @Override 
    public HashMap<String, String> call() { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("myvideoid", "1234"); 
        result.put("mysdkversion", Version.getVersion()); 
  
        return result; 
    } 
}); 
  
// Ad Metadata Block invoked on every ad start 
vaMetadata.setAdMetadataBlock(new VideoAnalyticsMetadata.AdMetadataBlock() { 
    @Override 
    public HashMap<String, String> call(Ad ad) { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("myadid", "ad-1234"); 
        result.put("myad-sdkversion", Version.getVersion()); 
  
        return result; 
    } 
}); 
  
// Chapter Metadata Block invoked on every chapter start 
vaMetadata.setChapterMetadataBlock(new VideoAnalyticsMetadata.ChapterMetadataBlock() { 
    @Override 
    public HashMap<String, String> call(VideoAnalyticsChapterData chapter) { 
        HashMap<String, String> result = new HashMap<String, String>(); 
        result.put("mychapterid", "chapter-1234"); 
        result.put("mychapter-sdkversion", Version.getVersion()); 
  
        return result; 
    } 
});
```
