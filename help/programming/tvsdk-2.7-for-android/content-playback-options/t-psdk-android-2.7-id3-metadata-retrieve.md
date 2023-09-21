---
description: Les balises ID3 fournissent des informations sur un fichier audio ou vidéo, telles que le titre du fichier ou le nom de l’artiste. TVSDK détecte les balises ID3 au niveau du segment du flux de transport (TS) dans les flux HLS et distribue un événement. L’application peut extraire des données de la balise .
title: Balises ID3
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Balises ID3 {#id-tags}

Les balises ID3 fournissent des informations sur un fichier audio ou vidéo, telles que le titre du fichier ou le nom de l’artiste. TVSDK détecte les balises ID3 au niveau du segment du flux de transport (TS) dans les flux HLS et distribue un événement. L’application peut extraire des données de la balise .

>[!IMPORTANT]
>
>TVSDK reconnaît les métadonnées ID3 (version 2.3.0 ou 2.4.0) dans les flux audio (AAC) et vidéo (H.264) dans l’un de ses encodages possibles (ASCII, UTF8, UTF16-BE ou UTF16-LE). Il ignore les balises ID3 qui ne se trouvent pas dans l’une des versions ou l’un des formats reconnus. Le codage non spécifié est traité comme UTF8.

Lorsque TVSDK détecte les métadonnées ID3, il émet une notification avec les données suivantes :

* TYPE = ID3
* NAME = ID3

1. Mise en oeuvre d’un écouteur d’événement pour `MediaPlayer.TimedMetadataEventListener#onTimedMetadata(TimeMetadata timeMetadata)` et l’enregistrer auprès de la fonction `MediaPlayer` .

   TVSDK appelle cet écouteur lorsqu’il détecte `ID3` métadonnées.

   >[!TIP]
   >
   >Les repères de publicité personnalisés utilisent le même `onTimedMetadata` pour indiquer la détection d’une nouvelle balise. Cela ne doit pas prêter à confusion, car des signaux publicitaires personnalisés sont détectés au niveau du manifeste et les balises ID3 sont incorporées dans le flux. Pour plus d’informations, voir [Balises personnalisées](../../tvsdk-2.7-for-android/ad-insertion/custom-tags-configure/c-psdk-android-2.7-custom-tags-configure.md).


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
