---
description: Vous pouvez utiliser plusieurs résolveurs de contenu pour gérer différentes opérations de chronologie.
seo-description: Vous pouvez utiliser plusieurs résolveurs de contenu pour gérer différentes opérations de chronologie.
seo-title: Résolveurs de contenu pour suppression/remplacement d’annonces
title: Résolveurs de contenu pour suppression/remplacement d’annonces
uuid: d43d54be-e04a-49dd-a695-e4e8f981ccb4
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Résolveurs de contenu pour suppression/remplacement d’annonces {#content-resolvers-for-ad-deletion-replacement}

Vous pouvez utiliser plusieurs résolveurs de contenu pour gérer différentes opérations de chronologie.

```java
public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { 
    List<ContentResolver> resolvers = new ArrayList<ContentResolver>(); 
    MediaPlayerItemConfig itemConfig = item.getConfig(); 
    if(itemConfig) { 
        CustomRangeMetadata customRanges = itemConfig.getCustomRangeMetadata(); 
        if (customRanges) { 
            List<ReplaceTimeRange> timeRanges = customRanges.getTimeRangeList(); 
 
            if (timeRanges && timeRanges.size() > 0) { 
                //CustomRangeResolver is activated by the presence of CustomRanges 
                resolvers.add(new CustomRangeResolver()); 
            } 
        } 
        AdvertisingMetadata metadata = itemConfig.getAdvertisingMetadata(); 
        if (metadata) { 
            if (metadata instanceOf AuditudeSettings)  
            resolvers.add(new AuditudeResolver(getContext());                                      
        } 
    } 
    //Add your custom resolver if any 
    resolvers.add(MyOpportunityGenerator(item)); 
    return resolvers; 
} 
```
