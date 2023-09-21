---
title: Détails de la notification NATIVE_ERROR
description: Détails de la notification NATIVE_ERROR
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Détails de la notification NATIVE_ERROR {#details-for-the-native-error-notification}

Lorsque TVSDK gère une erreur native, il définit certaines ou toutes les valeurs de clés de métadonnées suivantes.

<table id="table_86A21619515B435DBB65DC4DFBB64B29"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nom de la clé de métadonnées </th> 
   <th colname="col2" class="entry"> Valeur des métadonnées </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> NATIVE_ERROR_CODE </span> </td> 
   <td colname="col2"> 
    <pre>
      Code d’erreur natif de l’AVE. 
    </pre> Ces codes représentent les éléments suivants : 
    <ul id="ul_330C626DE27B45A09E8851CC24768A07"> 
     <li id="li_0845A9BBB55545BDB49BD4F4802C0E54">Erreurs DRM (codes 3300 à 3367). Ils sont identiques aux codes d’erreur de Flash Player équivalents. </li> 
     <li id="li_98A571480C154CF0AE1DC101FF0834C4">Erreurs de lecture vidéo (-1 à 89). </li> 
     <li id="li_D7C19955DEF94DA88B822C8C57D6D2F4">Erreurs de chiffrement (300 à 307). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> NATIVE_ERROR_NAME </span> </td> 
   <td colname="col2"> Chaîne contenant le nom de l’erreur, par exemple : <span class="codeph"> AAXS_InvalidVoucher </span> ou <span class="codeph"> DECODER_FAILED </span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> NATIVE_SUBERROR_CODE </span> </td> 
   <td colname="col2"> Pour les erreurs DRM, les codes de sous-erreur sont également renvoyés. Ces codes correspondent à la variable <span class="codeph"> DRMErrorEvents </span> code de sous-erreur renvoyé par le Flash Player. Lorsque vous signalez des erreurs à Adobe, incluez cette valeur numérique pour obtenir de l’aide. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> DRM_ERROR_STRING </span> </td> 
   <td colname="col2"> Pour DRM, il s’agit de votre chaîne d’erreur personnalisée issue du déploiement de votre serveur DRM, le cas échéant. Incluez également ce paramètre lors de la création de rapports d’erreurs à Adobe. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="col2"> Description de la chaîne de l’erreur. En règle générale, l’URL du média. </td> 
  </tr> 
 </tbody> 
</table>

TVSDK reçoit ces codes d’erreur et chaînes du moteur vidéo.

>[!IMPORTANT]
>
>Pour obtenir la liste complète des codes d’erreur client DRM Adobe Primetime, voir [Référence de message d’erreur du client DRM](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_client_error_message_reference.pdf).
