---
description: L’interface Codeur vidéo de l’AVE renvoie ces notifications de lecture vidéo dans l’objet de métadonnées NATIVE_ERROR.
title: Valeurs de lecture vidéo NATIVE_ERROR
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 6%

---

# NATIVE_ERROR : valeurs de lecture vidéo{#native-error-video-playback-values}

L’interface Codeur vidéo de l’AVE renvoie ces notifications de lecture vidéo dans l’objet de métadonnées NATIVE_ERROR.

<table> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Valeur de la clé de métadonnées RUNTIME_CODE </th> 
   <th colname="col2" class="entry"> Valeur de la clé de métadonnées RUNTIME_CODE_MESSAGE </th> 
   <th colname="col3" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> -1 </td> 
   <td colname="col2"><span class="codeph"> END_OF_PERIOD</span> </td> 
   <td colname="col3"> Fin de période. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 0 </td> 
   <td colname="col2"><span class="codeph"> SUCCÈS</span> </td> 
   <td colname="col3"> L'opération a réussi. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 1 </td> 
   <td colname="col2"> <span class="codeph"> ASYNC_OPERATION_IN_PROGRESS</span> </td> 
   <td colname="col3"> Opération asynchrone. La demande d’opération a été effectuée. Les informations de succès/échec seront disponibles ultérieurement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 2 </td> 
   <td colname="col2"><span class="codeph"> EOF</span> </td> 
   <td colname="col3"> Opération impossible en raison de la condition de fin de fichier (EOF). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3 </td> 
   <td colname="col2"><span class="codeph"> DECODER_FAILED</span> </td> 
   <td colname="col3"> Le décodeur a échoué à l’exécution. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 4 </td> 
   <td colname="col2"><span class="codeph"> DEVICE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Échec de l’ouverture du décodeur matériel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 5 </td> 
   <td colname="col2"><span class="codeph"> FILE_NOT_FOUND </span> </td> 
   <td colname="col3"> La ressource est introuvable. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 6 </td> 
   <td colname="col2"><span class="codeph"> GENERIC_ERROR </span> </td> 
   <td colname="col3"> Erreur générique. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 7 </td> 
   <td colname="col2"><span class="codeph"> IRRECOVERABLE_ERROR </span> </td> 
   <td colname="col3"> Une condition d’erreur à laquelle le moteur vidéo ne peut pas récupérer. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 8 </td> 
   <td colname="col2"><span class="codeph"> LOST_CONNECTION_RECOVERABLE </span> </td> 
   <td colname="col3"> Erreur réseau, tentative de récupération. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 9 </td> 
   <td colname="col2"><span class="codeph"> NO_FIXED_SIZE </span> </td> 
   <td colname="col3"> La taille de la ressource ne peut pas être déterminée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 10 </td> 
   <td colname="col2"><span class="codeph"> NOT_IMPLEMENTED </span> </td> 
   <td colname="col3"> Fonction non implémentée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 11 </td> 
   <td colname="col2"><span class="codeph"> OUT_OF_MEMORY </span> </td> 
   <td colname="col3"> Mémoire insuffisante. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 12 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR </span> </td> 
   <td colname="col3"> Erreur lors de l’analyse du fichier multimédia. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 13 </td> 
   <td colname="col2"><span class="codeph"> SIZE_UNKNOWN </span> </td> 
   <td colname="col3"> La ressource a une taille, mais elle est inconnue. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 14 </td> 
   <td colname="col2"><span class="codeph"> UNDER_FLOW </span> </td> 
   <td colname="col3"> Condition de sous-flux. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 15 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_CONFIG </span> </td> 
   <td colname="col3"> Configuration non prise en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 16 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_OPERATION </span> </td> 
   <td colname="col3"> Le fonctionnement n’est pas pris en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 17 </td> 
   <td colname="col2"><span class="codeph"> WAITING_FOR_INIT </span> </td> 
   <td colname="col3"> Pas encore initialisé. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 18 </td> 
   <td colname="col2"><span class="codeph"> INVALID_PARAMETER </span> </td> 
   <td colname="col3"> Paramètre non valide. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 19 </td> 
   <td colname="col2"><span class="codeph"> INVALID_OPERATION</span> </td> 
   <td colname="col3"> Opération non autorisée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 20 </td> 
   <td colname="col2"><span class="codeph"> OP_ONLY_ALLOWED_IN_PAUSED_STATE</span> </td> 
   <td colname="col3"> L’opération n’est autorisée que si elle est suspendue. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 21 </td> 
   <td colname="col2"><span class="codeph"> OP_INVALID_WITH_AUDIO_ONLY_FILE</span> </td> 
   <td colname="col3"> L’opération ne peut pas être utilisée sur des fichiers audio uniquement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 22 </td> 
   <td colname="col2"><span class="codeph"> PREVIOUS_STEP_SEEK_IN_PROGRESS</span> </td> 
   <td colname="col3"> L’opération de recherche précédente est toujours en cours. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 23 </td> 
   <td colname="col2"><span class="codeph"> SOURCE_NOT_SPECIFIED </span> </td> 
   <td colname="col3"> Ressource non spécifiée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 24 </td> 
   <td colname="col2"><span class="codeph"> RANGE_ERROR</span> </td> 
   <td colname="col3"> La valeur spécifiée est hors plage. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 25 </td> 
   <td colname="col2"><span class="codeph"> INVALID_SEEK_TIME</span> </td> 
   <td colname="col3"> Heure de recherche non valide. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 26 </td> 
   <td colname="col2"><span class="codeph"> FILE_STRUCTURE_INVALID</span> </td> 
   <td colname="col3"> Le fichier spécifié n’est pas conforme à la syntaxe attendue. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 27 </td> 
   <td colname="col2"><span class="codeph"> COMPONENT_CREATION_FAILURE</span> </td> 
   <td colname="col3"> Impossible de créer un composant essentiel. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 28 </td> 
   <td colname="col2"><span class="codeph"> DRM_INIT_ERROR</span> </td> 
   <td colname="col3"> Échec de la création du contexte DRM. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 29 </td> 
   <td colname="col2"><span class="codeph"> CONTAINER_NOT_SUPPORTED </span> </td> 
   <td colname="col3"> Le type de conteneur n’est pas pris en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 30 </td> 
   <td colname="col2"><span class="codeph"> SEEK_FAILED</span> </td> 
   <td colname="col3"> Échec de la recherche. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 31 </td> 
   <td colname="col2"><span class="codeph"> CODEC_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Code non pris en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 32 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_UNAVAILABLE</span> </td> 
   <td colname="col3"> Le réseau n’est pas disponible. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 33 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_ERROR</span> </td> 
   <td colname="col3"> Erreur lors de l’obtention des données du réseau. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 34 </td> 
   <td colname="col2"><span class="codeph"> DÉBORDEMENT</span> </td> 
   <td colname="col3"> Débordement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 35 </td> 
   <td colname="col2"><span class="codeph"> VIDEO_PROFILE_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> Profil vidéo non pris en charge </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 36 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_NOT_LOADED</span> </td> 
   <td colname="col3"> Une opération a été tentée sur une période HOLD ou une période qui n’a pas encore été chargée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 37 </td> 
   <td colname="col2"><span class="codeph"> INVALID_REPLACE_DURATION</span> </td> 
   <td colname="col3"> La durée de remplacement spécifiée n’est pas valide ou s’étend au-delà de la fin du flux. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 38 </td> 
   <td colname="col2"><span class="codeph"> CALLED_FROM_WRONG_THREAD</span> </td> 
   <td colname="col3"> L’API ne peut pas être appelée à partir du mauvais thread. Surtout pour les éléments d’API qui doivent être appelés à partir du thread principal uniquement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 39 </td> 
   <td colname="col2"><span class="codeph"> FRAGMENT_READ_ERROR</span> </td> 
   <td colname="col3"> Erreur de lecture du fragment. Aucun basculement n’est présent. Le moteur essaiera de lire le fragment suivant. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 40 </td> 
   <td colname="col2"><span class="codeph"> ABORDÉ</span> </td> 
   <td colname="col3"> L’opération a été abandonnée par un appel Abandon ou Détruire explicite. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 41 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_HLS_VERSION</span> </td> 
   <td colname="col3"> Impossible de lire cette version du média HLS. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 42 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_FAIL_OVER</span> </td> 
   <td colname="col3"> Impossible d’échouer. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 43 </td> 
   <td colname="col2"><span class="codeph"> HTTP_TIME_OUT</span> </td> 
   <td colname="col3"> Le téléchargement HTTP a expiré. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 44 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_DOWN </span> </td> 
   <td colname="col3"> La connexion réseau de l’utilisateur est hors service. La lecture peut s’arrêter à tout moment et reprendre lorsque la connexion est disponible. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 45 </td> 
   <td colname="col2"><span class="codeph"> NO_USABLE_BITRATE_PROFILE</span> </td> 
   <td colname="col3"> Aucun profil de débit utilisable trouvé dans la diffusion. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 46 </td> 
   <td colname="col2"><span class="codeph"> BAD_MANIFEST_SIGNATURE</span> </td> 
   <td colname="col3"> Le manifeste a une mauvaise signature. Le test de signature du manifeste a échoué. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 47 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_LOAD_PLAYLIST</span> </td> 
   <td colname="col3"> Impossible de charger une liste de lecture. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 48 </td> 
   <td colname="col2"><span class="codeph"> REPLACEMENT_FAILED</span> </td> 
   <td colname="col3"> Le remplacement spécifié dans une API d’insertion n’a pas réussi. Cela signifie que l’insertion a réussi, mais que le remplacement ne l’a pas été. Le remplacement peut échouer si le manifeste à remplacer a été supprimé de la chronologie. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 49 </td> 
   <td colname="col2"><span class="codeph"> SWITCH_TO_ASYMMETRIC_PROFILE</span> </td> 
   <td colname="col3"> DRM passe à un profil asymétrique. Tous les profils doivent être alignés dans la durée. Si ce n’est pas le cas, cet avertissement est généré et des sauts peuvent se produire dans la lecture. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 50 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_BACKWARD</span> </td> 
   <td colname="col3"> La fenêtre active ne doit être redirigée que vers l’avant. Si ce n’est pas le cas, cet avertissement s’affiche et la fenêtre n’est pas lue. Pour cette raison, il peut y avoir des sauts (ou une longue pause/arrêt) dans la lecture. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 51 </td> 
   <td colname="col2"><span class="codeph"> CURRENT_PERIOD_EXPIRED</span> </td> 
   <td colname="col3"> Fenêtre active déplacée au-delà de la période actuelle. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 52 </td> 
   <td colname="col2"><span class="codeph"> CONTENT_LENGTH_MISMATCH</span> </td> 
   <td colname="col3"> La longueur du contenu consignée par le serveur HTTP ne correspondait pas à la taille réelle du média. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 53 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_HOLD</span> </td> 
   <td colname="col3"> Le lecteur multimédia ne peut pas lire davantage, car il a atteint le délai défini par <span class="codeph"> setholdAt</span> API. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 54 </td> 
   <td colname="col2"><span class="codeph"> LIVE_HOLD </span> </td> 
   <td colname="col3"> Le lecteur multimédia ne peut pas charger les segments, car il a atteint la fin de la fenêtre active. Le chargement des segments reprend lorsque le serveur ajoute de nouveaux médias à la fenêtre active. Cet état est généralement atteint si : 
    <ul id="ul_FCFF658EDA4144E59970B317D6DEB624"> 
     <li id="li_2F6EEEB782D54CD999BC7CC7C0B78B48">La variable <span class="codeph"> bufferTime</span> est trop élevé (égal ou supérieur à la durée de la fenêtre active). </li> 
     <li id="li_25CE97115ED64E44AA89977FB5F0DCF7">Une combinaison d’une ou de plusieurs API d’insertion/suppression a remplacé plus de médias qu’elle n’en a ajouté. </li> 
     <li id="li_1B14716B2157492AB1859306D1250523">La période suivante est une période d’activation avec un remplacement de média en attente (en raison de <span class="codeph"> InsertBy</span> Appel API) </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 55 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_INTERLEAVING </span> </td> 
   <td colname="col3"> L’entrelacement audio et vidéo dans le média n’est pas effectué correctement. Il s’agit d’une erreur de package. L’avertissement est envoyé lorsque la différence dépasse deux secondes. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 56 </td> 
   <td colname="col2"><span class="codeph"> DRM_NOT_AVAILABLE</span> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 57 </td> 
   <td colname="col2"><span class="codeph"> PLAYBACK_NOT_AUTHORIZED</span> </td> 
   <td colname="col3"> La lecture HLS n’a pas été activée dans le Flash Player. Voir <span class="codeph"> AuthorizedFeatures.enableHLSPlayback</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 58 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_SAMPLE_FOUND</span> </td> 
   <td colname="col3"> Le décodeur a reçu un mauvais échantillon qui ne peut pas être décodé. Il ne s’agit généralement pas d’une erreur fatale, mais cela indique qu’il peut y avoir des problèmes dans l’audio/la vidéo. Trop d’instances de cette erreur indiquent un mauvais codage ou un fichier incorrect. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 59 </td> 
   <td colname="col2"><span class="codeph"> RANGE_SPANS_READ_HEAD</span> </td> 
   <td colname="col3"> Une fois la lecture lancée, la plage Insérer/Remplacer ne doit pas contenir le titre de lecture. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 60 </td> 
   <td colname="col2"><span class="codeph"> POSTROLL_WITH_LIVE_NOT_ALLOWED</span> </td> 
   <td colname="col3"> Les insertions post-roll ne sont pas autorisées sur un média en direct. Elles sont toutefois autorisées une fois que le serveur a marqué le média comme terminé. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 61 </td> 
   <td colname="col2"><span class="codeph"> INTERNAL_ERROR</span> </td> 
   <td colname="col3"> Un problème très rare qui ne devrait jamais se produire. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 62 </td> 
   <td colname="col2"><span class="codeph"> SPS_PPS_FOUND_OUTSIDE_AVCC</span> </td> 
   <td colname="col3"> Le flux ne suit pas la recommandation de package de toujours placer H264 SPS/PPS dans un AVCC. Des problèmes de recherche/lecture peuvent s’afficher. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 63 </td> 
   <td colname="col2"><span class="codeph"> PARTIAL_REPLACEMENT</span> </td> 
   <td colname="col3"> Le remplacement spécifié dans une API d’insertion n’a été que partiellement effectué. Cela se produit lorsque replaceDuration s’étend sur la durée de la chronologie. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 64 </td> 
   <td colname="col2"><span class="codeph"> RENDITION_M3U8_ERROR</span> </td> 
   <td colname="col3"> Une erreur de chargement s’est produite dans la liste de lecture du rendu. Il s’agit uniquement d’AVE, et non de FlashPlayer. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 65 </td> 
   <td colname="col2"><span class="codeph"> NULL_OPERATION</span> </td> 
   <td colname="col3"> L'opération ne fait rien. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 66 </td> 
   <td colname="col2"><span class="codeph"> SEGMENT_SKIPPED_ON_FAILURE</span> </td> 
   <td colname="col3"> Le segment ne peut pas être lu et est ignoré en cas d’échec. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 67 </td> 
   <td colname="col2"><span class="codeph"> INCOMPATIBLE_RENDER_MODE</span> </td> 
   <td colname="col3"> Mode de rendu non compatible. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 68 </td> 
   <td colname="col2"><span class="codeph"> PROTOCOL_NOT_SUPPORTED </span> </td> 
   <td colname="col3"> Le protocole Web utilisé dans l’URL n’est pas pris en charge. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 69 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR_INCOMPATIBLE_VERSION</span> </td> 
   <td colname="col3"> Erreur lors de l’analyse du fichier multimédia. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 70 </td> 
   <td colname="col2"><span class="codeph"> MANIFEST_FILE_UNEXPECTEDLY_CHANGED</span> </td> 
   <td colname="col3"> Le fichier de manifeste a été modifié de manière inattendue. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 71 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_SPLIT_TIMELINE</span> </td> 
   <td colname="col3"> Impossible d’effectuer une opération de partage sur une chronologie. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 72 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_ERASE_TIMELINE</span> </td> 
   <td colname="col3"> Impossible d’effectuer une opération d’effacement sur une chronologie. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 73 </td> 
   <td colname="col2"><span class="codeph"> DID_NOT_GET_NEXT_FRAGMENT</span> </td> 
   <td colname="col3"> N’a pas obtenu le fragment suivant. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 74 </td> 
   <td colname="col2"><span class="codeph"> NO_TIMELINE</span> </td> 
   <td colname="col3"> Aucune chronologie présente dans une structure de données interne. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 75 </td> 
   <td colname="col2"><span class="codeph"> LISTENER_NOT_FOUND</span> </td> 
   <td colname="col3"> Aucun écouteur trouvé dans une structure de données interne. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 76 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_START_ERROR</span> </td> 
   <td colname="col3"> Impossible de démarrer l’audio. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 77 </td> 
   <td colname="col2"><span class="codeph"> NO_AUDIO_SINK</span> </td> 
   <td colname="col3"> Aucun évier audio n’est présent dans une structure de données interne. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 78 </td> 
   <td colname="col2"><span class="codeph"> FILE_OPEN_ERROR</span> </td> 
   <td colname="col3"> Impossible d’ouvrir le fichier. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 79 </td> 
   <td colname="col2"><span class="codeph"> FILE_WRITE_ERROR</span> </td> 
   <td colname="col3"> Impossible d’écrire dans un fichier. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 80 </td> 
   <td colname="col2"><span class="codeph"> FILE_READ_ERROR</span> </td> 
   <td colname="col3"> Impossible de lire à partir d’un fichier. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 81 </td> 
   <td colname="col2"><span class="codeph"> ID3PARSE_ERROR</span> </td> 
   <td colname="col3"> Une erreur s’est produite lors de l’analyse des données ID3. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 82 </td> 
   <td colname="col2"><span class="codeph"> SECURITY_ERROR </span> </td> 
   <td colname="col3"> Le chargement du contenu a échoué en raison de restrictions de sécurité. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 83 </td> 
   <td colname="col2"><span class="codeph"> TIMELINE_TOO_SHORT</span> </td> 
   <td colname="col3"> La durée de la chronologie est trop courte. S’il s’agit d’une diffusion en direct, une mise en mémoire tampon fréquente peut se produire. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 84 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_START</span> </td> 
   <td colname="col3"> Le flux a été basculé vers un flux audio uniquement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 85 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_END</span> </td> 
   <td colname="col3"> Le flux est passé de l’audio uniquement à un flux vidéo. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 87 </td> 
   <td colname="col2"><span class="codeph"> KEY_NOT_FOUND </span> </td> 
   <td colname="col3"> Clé introuvable. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 88 </td> 
   <td colname="col2"><span class="codeph"> INVALID_KEY</span> </td> 
   <td colname="col3"> La clé n’est pas valide. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 89 </td> 
   <td colname="col2"> <span class="codeph"> KEY_SERVER_NOT_FOUND</span> </td> 
   <td colname="col3"> Le serveur de clés ne renvoie pas de clé. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 90 </td> 
   <td colname="col2"> <span class="codeph"> MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</span> </td> 
   <td colname="col3"> Impossible de gérer la mise à jour du manifeste principal. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 91 </td> 
   <td colname="col2"> <span class="codeph"> UNREPORTED_TIME_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Discontinuité de temps non signalé (PTS) trouvée. </td> 
  </tr> 
 </tbody> 
</table>
