---
description: Ce tableau fournit des informations détaillées sur les notifications de type ERROR.
seo-description: Ce tableau fournit des informations détaillées sur les notifications de type ERROR.
seo-title: Codes de notification d’ERREUR
title: Codes de notification d’ERREUR
uuid: 50624782-3d0b-4ac4-b883-355c1f7e9bff
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Codes de notification d’ERREUR{#error-notification-codes}

Ce tableau fournit des informations détaillées sur les notifications de type ERROR.

<!--<a id="section_D29404228F5E4B818642CBA6A0D39546"></a>-->

La plupart des erreurs contiennent des métadonnées appropriées, par exemple l’URL de la ressource dont le téléchargement a échoué. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans le contenu audio alternatif ou dans une publicité.

<table frame="all" colsep="1" rowsep="1" id="table_8B61210A406A45ACBE37FC29729DDE22"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Code </th> 
   <th colname="2" class="entry"> Nom </th> 
   <th colname="3" class="entry"> InnerNotification </th> 
   <th colname="4" class="entry"> Touches de métadonnées </th> 
   <th colname="5" class="entry"> Commentaires </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>DRM</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 100000 </span> </td> 
   <td colname="2"><span class="codeph"> DRM_ERROR </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> MAJOR_DRM_CODE DESCRIPTION </span><span class="codeph"> _MINOR_DRM_CODE </span><span class="codeph"> _MINOR </span> </td> 
   <td colname="5">Reportez-vous également à la section 106000 ( <span class="codeph"> NATIVE_ERROR</span>).
   </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Lecture</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_ERROR </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101004 </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_ERROR </span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="4"> </td> 
   <td colname="5"> <p>Une erreur s’est produite lors du téléchargement d’un fragment ou d’un segment (vidéo et audio). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101006 </span> </td> 
   <td colname="2"><span class="codeph"> SECURITY_ERROR </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008</span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> <span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de l'exécution d'une opération de mise en pause. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span><span class="codeph"> _DESIRED_SEEK_POSITION </span><span class="codeph"> _DESIRED_SEEK_PERIOD </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de l'exécution d'une opération de recherche. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101102 </span> </td> 
   <td colname="2"><span class="codeph"> PERIOD_INFO_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de la récupération des informations sur une période de contenu. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101103 </span> </td> 
   <td colname="2"><span class="codeph"> RETRIEVE_TIME_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de la tentative de récupération de la position de lecture. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101104 </span> </td> 
   <td colname="2"><span class="codeph"> GET_QOS_DATA_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de la tentative de récupération des informations QOS. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101200 </span> </td> 
   <td colname="2"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de la tentative de téléchargement des données. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ressource non valide </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102100 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_LOAD_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span><span class="codeph"> RESSOURCE </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors du chargement d'un élément de ressource. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102101 </span> </td> 
   <td colname="2"><span class="codeph"> ÉCHEC DE RESOURCE_PLACEMENT_ </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID </span> </td> 
   <td colname="5"> <p>Une erreur s’est produite lors du placement d’une ressource sur le plan de montage chronologique de lecture. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Traitement des publicités </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104000 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL </span> </td> 
   <td colname="3"><span class="codeph"> AD_METADATA_INVALID </span><span class="codeph"> AD_RESOLVER_INITIALIZATION_FAIL </span><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span><span class="codeph"> AD_RESOLVER_SERVER_ </span> </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> Aucun </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_ INVALIDE </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> </td> 
   <td colname="5"> <p>La résolution de la publicité a échoué en raison d'un format de métadonnées publicitaires non valide. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span> </td> 
   <td colname="5"> <p>Le module externe d'annonce n'a pas pu résoudre les publicités. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005 </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL </span> </td> 
   <td colname="3">Aucun</td> 
   <td colname="4"><span class="codeph"> PROPOSED_AD_BREAK</span> </td> 
   <td colname="5"> <p>La phase de résolution de publicité a échoué. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104006 </span> </td> 
   <td colname="2"><span class="codeph"> AD_ </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Native</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106000 </span> </td> 
   <td colname="2"><span class="codeph"> NATIVE_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> RUNTIME_CODE</span><span class="codeph"> RUNTIME_CODE_MESSAGE</span> RESOURCE_URL <span class="codeph"> RESOURCE_TYPE</span><span class="codeph"></span>  RESOURCE_ID<span class="codeph"></span> <p><b>Détails DRM :</b> </p> <span class="codeph"> DRM_ERROR_STRING</span><span class="codeph"> RUNTIME_SUBERROR_CODE</span> </td> 
   <td colname="5"> <p>La bibliothèque AVE de bas niveau a généré une erreur. </p> <p>Voir <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Détails des notifications</a> NATIVE_ERROR pour plus d’informations sur les valeurs de ces clés de métadonnées. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106001 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_CREATION_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de l'instanciation de la bibliothèque de bas niveau AVE. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106002 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RELEASE_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de la publication de la bibliothèque de bas niveau AVE. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106003 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESOURCES_RELEASE_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de la publication des ressources GPU utilisées par la bibliothèque AVE. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106004 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESET_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de la réinitialisation de la bibliothèque AVE. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106005 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_SET_ _ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de l'association d'un à la bibliothèque AVE. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Autre son</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 109000 </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_ERROR </span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="4"><span class="codeph"> AUDIO_TRACK_NAME </span><span class="codeph"> AUDIO_TRACK_LANGUAGE </span> </td> 
   <td colname="5"> <p>Une erreur liée à une piste audio s'est produite. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Générique</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 199999 </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> <p>Marque un  d’erreur générique. Non pas réellement émis par TVSDK. Il ne s’agit que d’un marqueur pour la fin de la plage de codes numériques correspondant aux  d’erreur TVSDK. </p> </td> 
  </tr> 
 </tbody> 
</table>

