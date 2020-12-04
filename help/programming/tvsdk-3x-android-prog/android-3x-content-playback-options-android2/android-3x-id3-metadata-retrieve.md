---
description: Les balises ID3 fournissent des informations sur un fichier audio ou vidéo, telles que le titre du fichier ou le nom de l’artiste. TVSDK détecte les balises ID3 au niveau du segment de flux de transport (TS) dans les flux HLS et distribue un événement. L’application peut extraire des données de la balise .
seo-description: Les balises ID3 fournissent des informations sur un fichier audio ou vidéo, telles que le titre du fichier ou le nom de l’artiste. TVSDK détecte les balises ID3 au niveau du segment de flux de transport (TS) dans les flux HLS et distribue un événement. L’application peut extraire des données de la balise .
seo-title: Balises ID3
title: Balises ID3
uuid: 96901223-81c7-49c7-bacf-7b4bbdff1691
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---


# Balises ID3 {#id-tags}

Les balises ID3 fournissent des informations sur un fichier audio ou vidéo, telles que le titre du fichier ou le nom de l’artiste. TVSDK détecte les balises ID3 au niveau du segment de flux de transport (TS) dans les flux HLS et distribue un événement. L’application peut extraire des données de la balise .

>[!IMPORTANT]
>
>TVSDK reconnaît les métadonnées ID3 (version 2.3.0 ou 2.4.0) dans les flux audio (AAC) et vidéo (H.264) dans n’importe quel de ses encodages possibles (ASCII, UTF8, UTF16-BE ou UTF16-LE). Il ignore les balises ID3 qui ne se trouvent pas dans l’une des versions ou formats reconnus. Le codage non spécifié est traité comme UTF8.

Lorsque TVSDK détecte les métadonnées ID3, il émet une notification contenant les données suivantes :

* TYPE = ID3
* NAME = ID3

1. Implémentez un écouteur de événement pour `MediaPlayer.TimedMetadataEventListener#onTimedMetadata(TimeMetadata timeMetadata)` et enregistrez-le avec l&#39;objet `MediaPlayer`.

   TVSDK appelle cet écouteur lorsqu’il détecte des métadonnées `ID3`.

   >[!TIP]
   >
   >Les indices publicitaires personnalisés utilisent le même événement `onTimedMetadata` pour indiquer la détection d’une nouvelle balise. Cela ne doit pas entraîner de confusion, car des indices publicitaires personnalisés sont détectés au niveau du manifeste et les balises ID3 sont incorporées dans le flux. Pour plus d’informations, voir [Balises personnalisées](../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/custom-tags-configure/android-3x-custom-tags-configure.md).

1. Récupérez les métadonnées.

   ```java
   @Override 
    public void onTimedMetadata(TimedMetadata timedMetadata) { 
       TimedMetadata.Type type = timedMetadata.getType(); 
       if (type.equals(TimedMetadata.Type.ID3)){ 
           long time = timeMetadata.getTime(); 
           Metadata metadata = timedMetadata.getMetadata(); 
           Set<String> keys = metadata.keySet(); 
           for (String key : keys){ 
               byte[] value = metadata.getByteArray(key); 
           } 
       } 
   }
   ```
