---
description: Votre application doit utiliser les objets PTTimedMetadata appropriés aux moments appropriés.
seo-description: Votre application doit utiliser les objets PTTimedMetadata appropriés aux moments appropriés.
seo-title: Stocker les objets de métadonnées minutés à mesure qu’ils sont distribués
title: Stocker les objets de métadonnées minutés à mesure qu’ils sont distribués
uuid: 38e72a9b-571a-48da-9c17-80be453e6a98
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Stocker les objets de métadonnées minutés au fur et à mesure de leur distribution {#store-timed-metadata-objects-as-they-are-dispatched}

Votre application doit utiliser les objets PTTimedMetadata appropriés aux moments appropriés.

Lors de l’analyse du contenu, qui se produit avant la lecture, TVSDK identifie les balises abonnées et avertit votre application de ces balises. L’heure associée à chaque `PTTimedMetadata` correspond à l’heure absolue du plan de montage chronologique de lecture.

Votre demande doit remplir les tâches suivantes :

1. Assurez le suivi de l’heure de lecture actuelle.
1. Correspond à l’heure de lecture actuelle aux objets `PTTimedMetadata` distribués.

1. Utilisez `PTTimedMetadata` où l’heure de début est égale à l’heure de lecture actuelle.

   >[!NOTE]
   >
   >Le code ci-dessous suppose qu&#39;il n&#39;y a qu&#39;une seule instance `PTTimedMetadata` à la fois. S’il existe plusieurs instances, l’application doit les enregistrer correctement dans un dictionnaire. Une méthode consiste à créer un tableau à un moment donné et à stocker toutes les instances de ce tableau.

   L&#39;exemple suivant montre comment enregistrer des objets `PTTimedMetadata` dans une balise `NSMutableDictionary (timedMetadataCollection)` en fonction de l&#39;heure de début de chaque `timedMetadata`.

   ```
   NSMutableDictionary *timedMetadataCollection; 
   
   - (void)onMediaPlayerSubscribedTagIdentified:(NSNotification *)notification 
   { 
       if (!timedMetadataCollection) 
       { 
           timedMetadataCollection = [[NSMutableDictionary alloc] init]; 
       } 
       NSDictionary *userInfo = [notification userInfo]; 
       PTTimedMetadata *timedMetadata = [(PTTimedMetadata *)[userInfo objectForKey:PTTimedMetadataKey] retain]; 
       if ([timedMetadata.name  isEqualToString: @"#EXT-OATCLS-SCTE35"]) 
       { 
            NSLog(@"Adding timedMetadata %@ to timedMetadataCollection with time                      
                    %f",timedMetadata.name,CMTimeGetSeconds(timedMetadata.time)); 
   
           NSNumber *timedMetadataStartTime = [NSNumber numberWithInt:(int)CMTimeGetSeconds(timedMetadata.time)]; 
           [timedMetadataCollection setObject:timedMetadata forKey:timedMetadataStartTime]; 
       } 
       [timedMetadata release]; 
   }
   ```

## Analyse des balises d’ID3 Nielsen {#example_3B51E9D4AF2449FAA8E804206F873ECF}

Pour extraire la balise ID3 à des fins d’analyse, utilisez la méthode `onMediaPlayerSubscribedTagIdentified` suivante :

```
(void)onMediaPlayerSubscribedTagIdentified:(NSNotification *)notification 
{ 
NSDictionary *userInfo = [notification userInfo]; 
PTTimedMetadata *timedMetadata = (PTTimedMetadata *)[userInfo objectForKey:PTTimedMetadataKey]; 
if (timedMetadata.type == PTTimedMetadataTypeID3) 
Unknown macro: { PTMetadata *metadata = (PTMetadata *)timedMetadata; NSString * nstr = [[NSString alloc] initWithFormat} 
 
}
```

Après avoir analysé la balise ID3, extrayez les métadonnées spécifiques à Nielsen à l’aide des éléments suivants :

```
    (NSString *)parseNielsenUrlFromID3Tag:(NSString *)str 
    { 
    /* ID3 tag <AVMetadataItem: 0x15e58e60, identifier=id3/PRIV, keySpace=org.id3, key class = __NSCFString, key=PRIV, commonKey=(null), extendedLanguageTag=(null), dataType=(null), time= {110265598/4410000 = 25.004} 
 
    , duration= 
    {INVALID} 
 
    , startDate=(null), extras= 
    { info = "www.nielsen.com/X100zdCIGeIlgZnkYj6UvQ==/pI-X5FFk07770SXf2ZbI6g==/CE0C6​1TsDo0jIrNn9N2yTPe6nVG3dHZHfgS52fJeQjf9fJCga9tj4OW4NXPZ9fI1mx0gfYUPBXnjqolHemZPtn_FCoNg​8Dqw8-Auruf15fU04pJfXTTN0IgZ4iWBmeRiPpS9X100zdCIGeIlgZnkYj6UvVjmPIdY5jyRQTA=/00000/21778/00"; } 
 
    , value length=1> 
    */ 
 
NSString *nielsenStr = nil; 
for (NSString *keyValuePairString in [str componentsSeparatedByString:@", "]) 
{ 
if([keyValuePairString rangeOfString:@"nielsen.com"].location != NSNotFound) 
{ // Nielsen NSRange start = [keyValuePairString rangeOfString:@"\""]; NSRange end = [keyValuePairString rangeOfString:@"\";"]; nielsenStr = [keyValuePairString substringWithRange:NSMakeRange(start.location + 1, end.location-start.location)]; } 
 
} 
return nielsenStr; 
}
```
