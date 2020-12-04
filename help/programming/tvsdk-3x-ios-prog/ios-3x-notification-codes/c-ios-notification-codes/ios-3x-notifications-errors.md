---
description: Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.
seo-description: Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.
seo-title: 'null'
title: 'null'
uuid: 20828188-817a-471c-acbc-aeb5f336356b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 5%

---


# Codes de notification d&#39;ERREUR {#error-notification-codes}

Ce tableau fournit des informations détaillées sur les notifications de type ERROR.

La plupart des erreurs contiennent des métadonnées pertinentes, par exemple l’URL de la ressource qui n’a pas pu être téléchargée. Certaines notifications contiennent des métadonnées pour indiquer si le problème s’est produit dans le contenu vidéo principal, dans l’autre contenu audio ou dans une publicité.

<table frame="all" colsep="1" rowsep="1" id="table_8B61210A406A45ACBE37FC29729DDE22"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Code</b></th> 
   <th colname="2" class="entry"><b>Nom</b></th> 
   <th colname="3" class="entry"><b>InnerNotification</b></th> 
   <th colname="4" class="entry"><b>Touches de métadonnées</b></th> 
   <th colname="5" class="entry"><b>Commentaires</b></th> 
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
   <td colname="1"><span class="codeph"> 100000  </span> </td> 
   <td colname="2"><span class="codeph"> DRM_ERROR  </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> MAJOR_DRM_CODE  </span><span class="codeph"> MINOR_DRM_CODE  </span><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"></td> 
  </tr> 
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
   <td colname="3"></td> 
   <td colname="4"></td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101001  </span> </td> 
   <td colname="2"><span class="codeph"> NATIVE_PLAYBACK_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span><span class="codeph"> INTERNAL_ERROR  </span><span class="codeph"> URL  </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008  </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION</span> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de l'exécution d'une opération de recherche. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009  </span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de l'exécution d'une opération de mise en pause. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101101  </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> PLAYER_NOT_READY  </span> </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> <p>  </p> <p>  </p>
    <!-- workaround for PDF having too much negative kerning in column 2 --> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Ressource non valide</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102000  </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_MEDIA_PLAYER_ITEM  </span> </td> 
   <td colname="3"> <p>Aucun </p> </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Traitement des publicités</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_ INVALIDE  </span> </td> 
   <td colname="3"> <span class="codeph"> AD_NOT_INSERTED</span> </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>Échec de la résolution de la publicité en raison d'un format de métadonnées publicitaires non valide. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005  </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="3"> <span class="codeph"> AD_NOT_INSERTED  </span> </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>La phase de résolution de publicité a échoué. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104006  </span> </td> 
   <td colname="2"><span class="codeph"> AD_INATTEIGNABLE  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> </td> 
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
   <td colname="4"> <span class="codeph"> INTERNAL_ERROR  </span> </td> 
   <td colname="5"> <p>Une erreur iOS de bas niveau s'est produite. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Configuration</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107002  </span> </td> 
   <td colname="2"><span class="codeph"> ERREUR SET_CC_VISIBILITY_  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de la tentative de modification de la visibilité des pistes CC. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107003  </span> </td> 
   <td colname="2"><span class="codeph"> ERREUR SET_CC_STYLING_ERROR  </span> </td> 
   <td colname="3"> <span class="codeph"> NATIVE_ERROR  </span> </td> 
   <td colname="4"> <p>Aucun </p> </td> 
   <td colname="5"> <p>Une erreur s'est produite lors de la tentative de modification des options de mise en forme pour les pistes CC. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Unique iOS</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170000  </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_VERSION_ INCOMPATIBLE  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> <span class="codeph"> AD_ASSET</span> </td> 
   <td colname="5"> <p>La version HLS des publicités est supérieure à la version HLS du contenu. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170001  </span> </td> 
   <td colname="2"><span class="codeph"> ARGUMENT_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> <p>Erreur d'argument </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170002  </span> </td> 
   <td colname="2"><span class="codeph"> M3U8_PARSER_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> <p>Impossible d'analyser m3u8. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170003  </span> </td> 
   <td colname="2"><span class="codeph"> WEBVTT_PARSER_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> <p>Impossible d'analyser Webvtt. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170004  </span> </td> 
   <td colname="2"><span class="codeph"> HLS_SEGMENT_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span><span class="codeph"> URL  </span><span class="codeph"> INTERNAL_ERROR  </span> </td> 
   <td colname="5"> <p>Le segment dépasse la bande passante spécifiée pour la variante. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170005  </span> </td> 
   <td colname="2"><span class="codeph"> MBR_MEDIASEQUENCE_OFFSYNC  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> <p>Le numéro de la séquence multimédia n'est pas synchronisé sur tous les flux HLS de ce MBR. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170006  </span> </td> 
   <td colname="2"><span class="codeph"> MANSING_FILE_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span><span class="codeph"> URL  </span><span class="codeph"> INTERNAL_ERROR  </span> </td> 
   <td colname="5"> <p>Fichier manquant ou ne répondant pas. </p> <p>HTTP 404 : Fichier introuvable. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170007  </span> </td> 
   <td colname="2"><span class="codeph"> AD_EMPTY_RESPONSE  </span> </td> 
   <td colname="3"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> <p>Impossible de récupérer les publicités. Réponse vide. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170008  </span> </td> 
   <td colname="2"><span class="codeph"> AD_TIMEOUT  </span> </td> 
   <td colname="3"><span class="codeph"> AD_INSERTION_FAIL  </span> </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> <p>Impossible de récupérer les publicités. Erreur de dépassement de délai. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170009  </span> </td> 
   <td colname="2"><span class="codeph"> SUBTITLES_TRACK_CHANGE_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> PLAYER_NOT_READY  </span> </td> 
   <td colname="4"> Aucun </td> 
   <td colname="5"> <p>Erreur lors de la modification du suivi des sous-titres. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170010  </span> </td> 
   <td colname="2"><span class="codeph"> SITECATALYST_ERROR  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION  </span> </td> 
   <td colname="5"> <p>Erreur SiteCatalyst. Voir la description. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 170011  </span> </td> 
   <td colname="2"><span class="codeph"> AD_CIBLE_DURATION_INCOMPATIBLE  </span> </td> 
   <td colname="3"> Aucun </td> 
   <td colname="4"> <span class="codeph"> AD_ASSET</span> </td> 
   <td colname="5"> <p>La DURÉE de CIBLE de la publicité est supérieure à la DURÉE de CIBLE du contenu. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>L&#39;ID d&#39;annonce et l&#39;URL peuvent être récupérés via `PTAdAsset` dans les métadonnées de notification avec la clé `AD_ASSET`.
>
>L&#39;attribut `[]` spécifie une clé facultative pour la notification.
