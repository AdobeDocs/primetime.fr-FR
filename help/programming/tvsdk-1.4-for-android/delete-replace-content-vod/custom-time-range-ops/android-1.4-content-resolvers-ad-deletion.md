---
description: Vous pouvez utiliser plusieurs résolutions de contenu pour gérer différentes opérations de chronologie.
seo-description: Vous pouvez utiliser plusieurs résolutions de contenu pour gérer différentes opérations de chronologie.
seo-title: Résolveurs de contenu pour la suppression/remplacement d’annonces
title: Résolveurs de contenu pour la suppression/remplacement d’annonces
uuid: 2954ce0f-aed2-4a85-8e53-d4e89d1497b6
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Résolveurs de contenu pour la suppression/remplacement d’annonces {#content-resolvers-for-ad-deletion-replacement}

Vous pouvez utiliser plusieurs résolutions de contenu pour gérer différentes opérations de chronologie.

```java
List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
MetadataNode metadata = (MetadataNode) resource.getMetadata(); 
if (metadata != null) { 
    if (metadata.containsKey(DefaultMetadataKeys.TIME_RANGES_METADATA_KEY.getValue())) { 
        String timeRangeType = metadata.getValue(DefaultMetadataKeys.TIME_RANGES_METADATA_KEY.getValue()); 
        if (timeRangeType.equals(TimeRangeCollection.TIME_RANGE_TYPE_DELETE)) { 
            contentResolvers.add(new DeleteContentResolver()); 
        } else if (timeRangeType.equals(TimeRangeCollection.TIME_RANGE_TYPE_REPLACE)) { 
            contentResolvers.add(new DeleteContentResolver()); 
        } else if (timeRangeType.equals(TimeRangeCollection.TIME_RANGE_TYPE_MARK)) { 
            contentResolvers.add(new CustomAdMarkersContentResolver()); 
        } 
    } 
    if (metadata.containsKey(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue())) { 
        contentResolvers.add(new AuditudeResolver(context)); 
    } else if (metadata.containsKey(DefaultMetadataKeys.JSON_METADATA_KEY.getValue())) { 
        contentResolvers.add(new MetadataResolver()); 
    } 
} 
return contentResolvers;
```

