---
description: Ce tableau fournit des informations détaillées sur les notifications de type ERROR.
seo-description: Ce tableau fournit des informations détaillées sur les notifications de type ERROR.
seo-title: Codes de notification d’erreur
title: Codes de notification d’erreur
uuid: cc21473d-924e-475d-96ea-352233f664ef
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 4%

---


# Codes de notification d’erreur{#error-notification-codes}

Ce tableau fournit des informations détaillées sur les notifications de type ERROR.

<!--<a id="section_D29404228F5E4B818642CBA6A0D39546"></a>-->

La plupart des erreurs contiennent des métadonnées pertinentes, par exemple l’URL de la ressource qui n’a pas pu être téléchargée. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans l’autre contenu audio ou dans une publicité.

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
   <td colname="1"><b>Lecture</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101000  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101004  </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_ERROR</span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR</span> </td> 
   <td colname="4"> </td> 
   <td colname="5"> Une erreur s'est produite lors du téléchargement d'un fragment ou d'un segment (vidéo et audio). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008  </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE  </span><span class="codeph"> DESIRED_SEEK_POSITION  </span><span class="codeph"> DESIRED_SEEK_PERIOD  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de l'exécution d'une opération de recherche. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009  </span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> Une erreur s'est produite lors de l'exécution d'une opération de mise en pause. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101102  </span> </td> 
   <td colname="2"><span class="codeph"> PERIOD_INFO_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la récupération d'informations sur une période de contenu. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101103  </span> </td> 
   <td colname="2"><span class="codeph"> RETRIEVE_TIME_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la tentative de récupération de la position de lecture. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101104  </span> </td> 
   <td colname="2"><span class="codeph"> GET_QOS_DATA_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la tentative de récupération des informations QOS. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101200  </span> </td> 
   <td colname="2"><span class="codeph"> DOWNLOAD_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> URL  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la tentative de téléchargement des données. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ressource non valide</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102100  </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_LOAD_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span><span class="codeph"> RESSOURCE  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors du chargement d'un élément de ressource. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102101  </span> </td> 
   <td colname="2"><span class="codeph"> ÉCHEC DE RESOURCE_PLACEMENT_  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors du placement d'une ressource sur le plan de montage chronologique de lecture. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Traitement des publicités</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104000  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> AD_METADATA_INVALID  </span><span class="codeph"> AD_RESOLVER_INITIALIZATION_FAIL  </span><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL  </span><span class="codeph"> AD_RESOLVER_SERVER_INATTEIGNABLE  </span> </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> Aucun </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_ INVALIDE  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> Échec de la résolution de la publicité en raison d'un format de métadonnées publicitaires non valide. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104003  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE  </span> </td> 
   <td colname="5"> Le plug-in publicitaire n'a pas réussi à résoudre les publicités. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005  </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> PROPOSED_AD_BREAK</span> </td> 
   <td colname="5"> La phase de résolution de publicité a échoué. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>natif</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106000  </span> </td> 
   <td colname="2"><span class="codeph"> NATIVE_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> <span class="codeph"> NATIVE_ERROR_CODE  </span> <span class="codeph"> NATIVE_ERROR_NAME  </span> <span class="codeph"> DESCRIPTION  </span> <span class="codeph"> DESCRIPTION</span> <p><b>Détails du DRM :</b> </p> <span class="codeph"> DRM_ERROR_</span> <span class="codeph"> STRINGNATIVE_SUBERROR_CODE</span> </td> 
   <td colname="5"> <p>La bibliothèque AVE de bas niveau a généré une erreur. </p> <p>Voir <a href="../../../tvsdk-1.4-for-android/android-1.4-tvsdk-notification/notification-codes/native-error-summary/android-1.4-native-error-summary.md" format="html" scope="external"> Détails des notifications NATIVE_ERROR</a> pour plus d'informations sur les valeurs de ces clés de métadonnées. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106001  </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_CREATION_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de l'instanciation de la bibliothèque de bas niveau AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106002  </span> </td> 
   <td colname="2"><span class="codeph"> ERREUR ENGINE_RELEASE_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la publication de la bibliothèque de bas niveau AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106003  </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESOURCES_RELEASE_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la publication des ressources GPU utilisées par la bibliothèque AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106004  </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESET_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la réinitialisation de la bibliothèque AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106005  </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_SET_VUE_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> Une erreur s'est produite lors de l'attachement d'une vue à la bibliothèque AVE. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Configuration</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107000  </span> </td> 
   <td colname="2"><span class="codeph"> SET_VOLUME_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> VOLUME DE DESCRIPTION  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la tentative de définition du niveau de volume. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107001  </span> </td> 
   <td colname="2"><span class="codeph"> ERREUR SET_BUFFER_TIME_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span><span class="codeph"> PLAY_BUFFER_TIME  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la tentative de modification des paramètres de mise en mémoire tampon. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107002  </span> </td> 
   <td colname="2"><span class="codeph"> ERREUR SET_CC_VISIBILITY_  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la tentative de modification de la visibilité des pistes CC. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107003  </span> </td> 
   <td colname="2"><span class="codeph"> ERREUR SET_CC_STYLING_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la tentative de modification des options de mise en forme pour les pistes CC. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107004  </span> </td> 
   <td colname="2"><span class="codeph"> SET_ABR_PARAMETERS_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la tentative de modification des paramètres de contrôle ABR. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107005  </span> </td> 
   <td colname="2"><span class="codeph"> SET_BUFFER_ PARAMETERS_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span><span class="codeph"> INITIAL_BUFFER_TIME  </span><span class="codeph"> PLAY_BUFFER_TIME  </span> </td> 
   <td colname="5"> Une erreur s'est produite lors de la tentative de modification des paramètres de contrôle de mise en mémoire tampon. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Autre son</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 109000  </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_ERROR  </span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR  </span> </td> 
   <td colname="4"><span class="codeph"> AUDIO_TRACK_NAME  </span><span class="codeph"> AUDIO_TRACK_LANGUAGE  </span> </td> 
   <td colname="5"> Une erreur liée à une piste audio s'est produite. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Générique</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 19999  </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_ERROR</span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> Marque un événement d’erreur générique. Non pas réellement émis par TVSDK. Il s’agit uniquement d’un marqueur pour la fin de la plage de codes numériques correspondant aux événements d’erreur TVSDK. </td> 
  </tr> 
 </tbody> 
</table>

