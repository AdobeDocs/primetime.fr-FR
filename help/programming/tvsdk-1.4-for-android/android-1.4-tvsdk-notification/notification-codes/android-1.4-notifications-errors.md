---
description: Ce tableau fournit des informations détaillées sur les notifications de type ERROR.
title: Codes de notification d’erreur
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 4%

---

# Codes de notification d’erreur{#error-notification-codes}

Ce tableau fournit des informations détaillées sur les notifications de type ERROR.

<!--<a id="section_D29404228F5E4B818642CBA6A0D39546"></a>-->

La plupart des erreurs contiennent des métadonnées pertinentes, par exemple l’URL de la ressource dont le téléchargement a échoué. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans le contenu audio alternatif ou dans une publicité.

<table frame="all" colsep="1" rowsep="1" id="table_8B61210A406A45ACBE37FC29729DDE22"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Code </th> 
   <th colname="2" class="entry"> Nom </th> 
   <th colname="3" class="entry"> InnerNotification </th> 
   <th colname="4" class="entry"> Clés de métadonnées </th> 
   <th colname="5" class="entry"> Commentaires </th> 
  </tr> 
 </thead>
 <tbody> 
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
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101004 </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_ERROR</span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR</span> </td> 
   <td colname="4"> </td> 
   <td colname="5"> Une erreur s’est produite lors du téléchargement d’un fragment ou d’un segment (vidéo et audio). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span><span class="codeph"> DESIRED_SEEK_POSITION </span><span class="codeph"> DESIRED_SEEK_PERIOD </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de l’exécution d’une opération de recherche. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009 </span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> Une erreur s’est produite lors de l’exécution d’une opération de pause. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101102 </span> </td> 
   <td colname="2"><span class="codeph"> PERIOD_INFO_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la récupération d’informations sur une période de contenu. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101103 </span> </td> 
   <td colname="2"><span class="codeph"> RETRIEVE_TIME_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la tentative de récupération de la position de lecture. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101104 </span> </td> 
   <td colname="2"><span class="codeph"> GET_QOS_DATA_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la tentative de récupération des informations QOS. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101200 </span> </td> 
   <td colname="2"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la tentative de téléchargement de données. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ressource non valide</b> </td> 
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
   <td colname="5"> Une erreur s’est produite lors du chargement d’un élément de ressource. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102101 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_PLACEMENT_FAILED </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID </span> </td> 
   <td colname="5"> Une erreur s’est produite lors du placement d’une ressource sur la chronologie de lecture. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Traitement des publicités</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104000 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL </span> </td> 
   <td colname="3"><span class="codeph"> AD_METADATA_INVALID </span><span class="codeph"> AD_RESOLVER_INITIALIZATION_FAIL </span><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span><span class="codeph"> AD_RESOLVER_SERVER_UNREACHABLE </span> </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> Aucun </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_ INVALID </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> La résolution de la publicité a échoué en raison d’un format de métadonnées de publicité non valide. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span> </td> 
   <td colname="5"> Le module externe d’annonce n’a pas pu résoudre les publicités. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005 </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> PROPOSED_AD_BREAK</span> </td> 
   <td colname="5"> La phase de résolution de la publicité a échoué. </td> 
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
   <td colname="4"> <span class="codeph"> NATIVE_ERROR_CODE </span> <span class="codeph"> NATIVE_ERROR_NAME </span> <span class="codeph"> DESCRIPTION </span> <span class="codeph"> DESCRIPTION</span> <p><b>Détails DRM :</b> </p> <span class="codeph"> DRM_ERROR_STRING</span> <span class="codeph"> NATIVE_SUBERROR_CODE</span> </td> 
   <td colname="5"> <p>La bibliothèque AVE de bas niveau a généré une erreur. </p> <p>Voir <a href="../../../tvsdk-1.4-for-android/android-1.4-tvsdk-notification/notification-codes/native-error-summary/android-1.4-native-error-summary.md" format="html" scope="external"> Détails des notifications NATIVE_ERROR</a> pour plus d’informations sur les valeurs de ces clés de métadonnées. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106001 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_CREATION_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de l’instanciation de la bibliothèque de bas niveau AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106002 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RELEASE_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la publication de la bibliothèque de bas niveau AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106003 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESOURCES_RELEASE_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la publication des ressources GPU utilisées par la bibliothèque AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106004 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_REET_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la réinitialisation de la bibliothèque AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106005 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_SET_VIEW_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> Une erreur s’est produite lors de l’ajout d’une vue à la bibliothèque AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Configuration</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107000 </span> </td> 
   <td colname="2"><span class="codeph"> SET_VOLUME_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> VOLUME DE DESCRIPTION </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la tentative de définition du niveau de volume. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107001 </span> </td> 
   <td colname="2"><span class="codeph"> SET_BUFFER_TIME_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span><span class="codeph"> PLAY_BUFFER_TIME </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la tentative de modification des paramètres de mise en mémoire tampon. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107002 </span> </td> 
   <td colname="2"><span class="codeph"> SET_CC_VISIBILITY_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la tentative de modification de la visibilité des suivis CC. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107003 </span> </td> 
   <td colname="2"><span class="codeph"> SET_CC_STYLING_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la tentative de modification des options de style pour les suivis CC. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107004 </span> </td> 
   <td colname="2"><span class="codeph"> SET_ABR_PARAMETERS_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la tentative de modification des paramètres de contrôle ABR. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107005 </span> </td> 
   <td colname="2"><span class="codeph"> SET_BUFFER_PARAMETERS_ERROR </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span><span class="codeph"> INITIAL_BUFFER_TIME </span><span class="codeph"> PLAY_BUFFER_TIME </span> </td> 
   <td colname="5"> Une erreur s’est produite lors de la tentative de modification des paramètres de contrôle de mise en mémoire tampon. </td> 
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
   <td colname="5"> Une erreur liée à une piste audio s’est produite. </td> 
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
   <td colname="2"><span class="codeph"> GENERIC_ERROR</span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> Marque un événement d’erreur générique. Non émis par TVSDK. Il ne s’agit que d’un marqueur pour la fin de la plage de codes numériques correspondant aux événements d’erreur TVSDK. </td> 
  </tr> 
 </tbody> 
</table>
