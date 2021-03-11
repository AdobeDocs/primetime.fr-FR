---
description: Les balises ID3 fournissent des informations sur un fichier audio ou vidéo, telles que le titre du fichier ou le nom de l’artiste. Le navigateur TVSDK détecte les balises ID3 au niveau du segment de flux de transport (TS) dans les flux HLS et distribue un événement. L’application peut extraire des données de la balise .
title: Balises ID3
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# ID3 balises{#id-tags}

Les balises ID3 fournissent des informations sur un fichier audio ou vidéo, telles que le titre du fichier ou le nom de l’artiste. Le navigateur TVSDK détecte les balises ID3 au niveau du segment de flux de transport (TS) dans les flux HLS et distribue un événement. L’application peut extraire des données de la balise .

Lorsqu’une nouvelle métadonnées ID3 est trouvée dans le flux HLS sous-jacent, le navigateur TVSDK déclenche un événement `AdobePSDK.TimedMetadataEvent`.

L’objet `TimedMetadata` pour ID3 possède les propriétés suivantes :

<table id="table_6C61886187FB44B4B9821E4B00200018"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nom de la propriété </th> 
   <th colname="col2" class="entry"> Détails </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> type  </span> </p> </td> 
   <td colname="col2"> <p>Type d’objet <span class="codeph"> TimedMetadata </span>. </p> <p>Pour les métadonnées ID3, la valeur est <span class="codeph"> AdobePSDK.TimedMetadataType.ID3 </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> time  </span> </p> </td> 
   <td colname="col2"> <p> Heure du lecteur à laquelle ces métadonnées temporisées ont été détectées. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id  </span> </p> </td> 
   <td colname="col2"> <p>ID de l’objet <span class="codeph"> TimedMetadata </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> name </span> </p> </td> 
   <td colname="col2"> <p>Nom de l’objet <span class="codeph"> TimedMetadata </span>. Pour les métadonnées ID3, la valeur est "ID3". </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> content  </span> </p> </td> 
   <td colname="col2"> <p>Contenu des métadonnées temporisées. Pour les balises ID3, cette valeur représente le tableau d’octets sérialisés. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> metadata  </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> Informations  </span> traitées TimedMetadata, qui est une instance d’ <span class="codeph"> AdobePSDK.Metadata  </span> où les images ID3 sont stockées. </p> <p> <p>Remarque :  Pour la balise Safari <span class="codeph"> video </span>, les données d’image particulières de la balise ID3 sont exposées sous la forme d’un objet par le biais d’un objet <span class="codeph"> AdobePSDK.Metadata </span> tandis que pour les autres navigateurs, les données d’image de la balise ID3 sont exposées sous la forme d’un tableau d’octets par le biais de l’objet <span class="codeph"> AdobePSDK.Metadata </span>. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

&#x200B;

Les différentes balises ID3 stockées dans `TimedMetadata` peuvent être récupérées par l’application de deux manières différentes :

* Dans l’écouteur de événement AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE.

   ```
   var isSafari = function () { 
       var nAgt = navigator.userAgent; 
       var appName = navigator.appName; 
       if ((nAgt.indexOf('MSIE') === -1) && //is not MS IE 
           (appName !== 'Netscape' || nAgt.indexOf('Trident/') === -1) && //is not MS IE11 
           (appName !== 'Netscape' || nAgt.indexOf('Edge') === -1) && // is not edge 
           (nAgt.indexOf('Chrome') === -1) && // is not chrome 
           (nAgt.indexOf('Safari') !== -1) //is Safari 
       ){ 
           return true; 
       } 
       return false; 
   }; 
   var hex2a = function (hex, offset, max) { 
       var str = ''; 
       if (!hex) 
           return str; 
       for (var i = offset; i < hex.length && i < offset + max; i++) 
           str += String.fromCharCode(hex[i]); 
       return str; 
   }; 
   var mediaPlayer = new AdobePSDK.MediaPlayer(); 
   mediaPlayer.addEventListener( AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE ,function(event){ 
       var td = event.timedMetadata; 
       if(td.type == AdobePSDK.TimedMetadataType.ID3){ 
           var md = td.metadata; 
           var keySet = md.keySet; 
           var onSafari = isSafari(); 
           if(keySet && keySet.length){ 
               var msg = ''; 
               for(var j = 0; j < keySet.length; j++){ 
                   var idTag = keySet[j]; 
                   msg += idTag; 
                   if(idTag.indexOf("T") == 0){ 
                       /* text frame*/ 
                       if(onSafari){ 
                           /* text frame data is exposed in object format 
                            * where corresponding text data is exposed through 
                            * data key of text frame data object 
                            * */ 
                           var frameDataObject = md.getObject(idTag); 
                           msg += " : " + frameDataObject.data; 
                       } else { 
                           var buff = md.getByteArray(idTag); 
                           msg += " : " + hex2a(buff, 0, buff.length - 1); 
                       } 
                   } 
                   msg += " ; "; 
               } 
           } 
       } 
   }); 
   ```

* Utilisation de la propriété `timedMetadata` de `MediaPlayerItem`.

   ```
   var isSafari = function () { 
       var nAgt = navigator.userAgent; 
       var appName = navigator.appName; 
       if ((nAgt.indexOf('MSIE') === -1) && //is not MS IE 
           (appName !== 'Netscape' || nAgt.indexOf('Trident/') === -1) && //is not MS IE11 
           (appName !== 'Netscape' || nAgt.indexOf('Edge') === -1) && // is not edge 
           (nAgt.indexOf('Chrome') === -1) && // is not chrome 
           (nAgt.indexOf('Safari') !== -1) //is Safari 
       ){ 
           return true; 
       } 
       return false; 
   }; 
   var hex2a = function (hex, offset, max) { 
       var str = ''; 
       if (!hex) 
           return str; 
       for (var i = offset; i < hex.length && i < offset + max; i++) 
           str += String.fromCharCode(hex[i]); 
       return str; 
   }; 
   var timedMetadataList = player.currentItem.timedMetadata; 
   for(var i = 0; i < timedMetadataList.length; i++){ 
       var td = timedMetadataList[i]; 
       if(td.type == AdobePSDK.TimedMetadataType.ID3){ 
           var md = td.metadata; 
           var keySet = md.keySet; 
           var onSafari = isSafari(); 
           if(keySet && keySet.length){ 
               var msg = ''; 
               for(var j = 0; j < keySet.length; j++){ 
                   var idTag = keySet[j]; 
                   msg += idTag; 
                   if(idTag.indexOf("T") == 0){ 
                       /* text frame*/ 
                       if(onSafari){ 
                           /* text frame data is exposed in object format 
                            * where corresponding text data is exposed through 
                            * data key of text frame data object 
                            * */ 
                           var frameDataObject = md.getObject(idTag); 
                           msg += " : " + frameDataObject.data; 
                       } else { 
                           var buff = md.getByteArray(idTag); 
                           msg += " : " + hex2a(buff, 0, buff.length - 1); 
                       } 
                   } 
                   msg += " ; "; 
               } 
           } 
       } 
   } 
   ```

