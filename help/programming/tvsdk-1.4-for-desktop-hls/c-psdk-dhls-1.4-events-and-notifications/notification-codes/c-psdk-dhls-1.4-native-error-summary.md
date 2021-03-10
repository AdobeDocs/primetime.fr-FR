---
title: Détails de la notification NATIVE_ERROR
description: Détails de la notification NATIVE_ERROR
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Détails de la notification NATIVE_ERROR {#details-for-the-native-error-notification}

Lorsque TVSDK gère une erreur native, il définit certaines ou toutes les valeurs de clés de métadonnées suivantes.

<table id="table_86A21619515B435DBB65DC4DFBB64B29"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nom de la clé de métadonnées </th> 
   <th colname="col2" class="entry"> Valeur de métadonnées </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_CODE  </span> </td> 
   <td colname="col2"> 
    <pre>
      Code d’erreur natif du Flash Player. 
    </pre> Ces codes représentent les éléments suivants : 
    <ul id="ul_330C626DE27B45A09E8851CC24768A07"> 
     <li id="li_0845A9BBB55545BDB49BD4F4802C0E54">Erreurs DRM (codes 3300 à 3367). Il s’agit des mêmes codes d’erreur de Flash Player équivalents. </li> 
     <li id="li_98A571480C154CF0AE1DC101FF0834C4">Erreurs de lecture vidéo (-1 à 89). </li> 
     <li id="li_D7C19955DEF94DA88B822C8C57D6D2F4">Erreurs de chiffrement (300 à 307). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_CODE_MESSAGE  </span> </td> 
   <td colname="col2"> Chaîne contenant le nom de l'erreur ; par exemple, <span class="codeph"> AAXS_InvalidVoucher </span> ou <span class="codeph"> DECODER_FAILED </span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_SUBERROR_CODE  </span> </td> 
   <td colname="col2"> Pour les erreurs DRM, les codes de sous-erreur sont également renvoyés. Ces codes correspondent au code de sous-erreur <span class="codeph"> DRMErrorEvents </span> renvoyé par le Flash Player. Si des erreurs de rapports sont signalées à l’Adobe, incluez cette valeur numérique pour obtenir de l’aide au dépannage. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> DRM_ERROR_STRING  </span> </td> 
   <td colname="col2"> Pour DRM, il s’agit de votre chaîne d’erreur personnalisée issue du déploiement de votre serveur DRM, si vous en avez défini une. Incluez également cette option lorsque des erreurs de rapports sont signalées à l’Adobe. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="col2"> Description de la chaîne de l'erreur. En général, l’URL du média. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_URL  </span> </td> 
   <td colname="col2"> URL du média. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_TYPE  </span> </td> 
   <td colname="col2"> Type de média (HLS). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_ID  </span> </td> 
   <td colname="col2"> ID du média. </td> 
  </tr> 
 </tbody> 
</table>

TVSDK reçoit ces codes d’erreur et ces chaînes du moteur vidéo.

>[!IMPORTANT]
>
>Pour une liste complète des codes d’erreur client DRM Adobe Primetime, voir [Guide de référence des messages d’erreur client DRM](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_client_error_message_reference.pdf).