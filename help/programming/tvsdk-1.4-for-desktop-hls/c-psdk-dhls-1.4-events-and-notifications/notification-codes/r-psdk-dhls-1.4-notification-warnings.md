---
description: Ce tableau présente des informations détaillées sur WARN. notifications de type.
seo-description: Ce tableau présente des informations détaillées sur WARN. notifications de type.
seo-title: AVERTISSEMENT des codes de notification
title: AVERTISSEMENT des codes de notification
uuid: 1ce5be07-f5bf-443c-b907-9768633e1300
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 2%

---


# Codes de notification d&#39;AVERTISSEMENT{#warning-notification-codes}

Ce tableau présente des informations détaillées sur WARN. notifications de type.

<!--<a id="section_F25366B6703040E3ADA993C113618F01"></a>-->

La plupart des avertissements contiennent des métadonnées pertinentes, par exemple l’URL de la ressource qui n’a pas été téléchargée. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans l’autre contenu audio ou dans une publicité.

<table frame="all" colsep="1" rowsep="1" id="table_C24772DF203B4DB2ACE6B475698C4C58"> 
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
   <td colname="1"><span class="codeph"> 200000  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_OPERATION_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> AUDIO_TRACK_ERROR  </span><span class="codeph"> SEEK_ERROR  </span> </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> <p>Une opération liée à la lecture a échoué, mais la lecture peut continuer. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Résolution de la publicité  </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201000  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> AD_RESOLVER_ RESOLVE_FAIL  </span><span class="codeph"> RESOURCE_PLACEMENT_ ÉCHOUÉ  </span><span class="codeph"> AD_RESOLVER_ METADATA_INVALID  </span> </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>Le résolveur d'annonces n'a pas pu résoudre/insérer le contenu de l'annonce. La lecture peut continuer. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Manifestations de fond</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204000  </span> </td> 
   <td colname="2"><span class="codeph"> ARRIÈRE-PLAN_MANIFEST_AVERTISSEMENT</span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> BACKGROUND_MANIFEST_ WARNING_</span> <span class="codeph"> ERRORBACKGROUND_MANIFEST_ WARNING_</span> <span class="codeph"> NAMEDESCRIPTION</span> </td> 
   <td colname="5"> <p> Erreur lors du téléchargement du manifeste en arrière-plan. Tout problème de mise à jour du manifeste en arrière-plan est distribué en tant qu’avertissement TVSDK et n’entraîne pas l’arrêt de la lecture. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204001  </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_SEEK_WARNING</span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> <p> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>natif</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"><span class="codeph"> 209100  </span> </td> 
   <td colname="2" morerows="1"><span class="codeph"> NATIVE_WARNING  </span> </td> 
   <td colname="3" morerows="1"> <p>Aucun </p> </td> 
   <td colname="4"><b>AVE</b> <p><span class="codeph"> NATIVE_ERROR_CODE  </span><span class="codeph"> NATIVE_ERROR_NAME  </span><span class="codeph"> DESCRIPTION  </span> </p> </td> 
   <td colname="5"> <p>La bibliothèque AVE de bas niveau a généré une erreur. </p> <p>Voir <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Détails des notifications NATIVE_ERROR</a> pour obtenir des informations détaillées sur les valeurs de ces champs de métadonnées. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="4"><b>DRM</b> <p><span class="codeph"> NATIVE_SUBERROR_</span> <span class="codeph"> CODEDRM_ERROR_STRING</span> </p> </td> 
   <td colname="5">Code d'erreur secondaire DRM et chaîne d'erreur du serveur DRM. Voir <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> Détails des notifications NATIVE_ERROR</a> pour obtenir des informations détaillées sur les valeurs de ces champs de métadonnées.
   </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Générique</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 299999  </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_WARNING  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>Marque un événement d’avertissement générique. Non pas réellement émis par TVSDK. Il s’agit simplement d’un marqueur pour la fin de la plage de codes numériques correspondant aux événements d’avertissement. </p> </td> 
  </tr> 
 </tbody> 
</table>

