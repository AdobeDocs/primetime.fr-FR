---
description: Vous pouvez utiliser les informations suivantes pour vous aider à habiller votre lecteur. Pour chaque construction visuelle, les comportements correspondants sont mentionnés dans le comportement par défaut.
seo-description: Vous pouvez utiliser les informations suivantes pour vous aider à habiller votre lecteur. Pour chaque construction visuelle, les comportements correspondants sont mentionnés dans le comportement par défaut.
seo-title: Esquisse le lecteur
title: Esquisse le lecteur
uuid: 516ff846-d76d-4062-b64b-3032f7a70470
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Esquisse le lecteur {#skinning-the-player}

Vous pouvez utiliser les informations suivantes pour vous aider à habiller votre lecteur. Pour chaque construction visuelle, les comportements correspondants sont mentionnés dans le comportement par défaut.

>[!IMPORTANT]
>
>Les détails d’habillage de ce concernent les éléments d’interface utilisateur par défaut créés par la structure de l’interface utilisateur. Si votre lecteur a modifié ces éléments, les éléments d’habillage doivent également être modifiés.

##  divs {#section_99B0D598219D4150B57E97D5381B118F}

Voici les styles des  divs de :

>[!TIP]
>
>Ces divs sont répertoriés dans le `common-styles.css` fichier.

Voici les styles de la div principale :

<table id="table_AC5745DF725543ADBBCD68BA6130DF12"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>Div principal</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-main-video-div-style</span> </td> 
   <td colname="col2"> <p>Style de la vidéo principale dans laquelle la vidéo est lue. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .pip-mode-active</span> </td> 
   <td colname="col2"> <p>Utilisé lorsque le mode PIP est actif. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Le comportement par défaut est <span class="codeph"> videoBehavior</span>. </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Image dans l’image (PIP)</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-pip-video-div</span> </td> 
   <td colname="col2"> <p>Style de la balise div dans laquelle la vidéo PIP est lue. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .-en-tant--vidéo-principale</span> </td> 
   <td colname="col2"> <p>Appliqué au fichier PIP initial lorsqu’il a été modifié et s’affiche comme vidéo principale. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>multi-vidéo</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> -.ptp-multi-</span> </td> 
   <td colname="col2"> <p>Est utilisé dans le  multi-vidéo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> -.ptp-multi-</span> </td> 
   <td colname="col2"> <p>Style CSS commun placé sur chaque vidéo dans la vue multiple. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multiview</span> </td> 
   <td colname="col2"> <p>Lorsque le qui héberge chacune des vidéos dans la vue multiple est dans la vue multiple. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Contrôles variés {#section_E9E4A8E3AEBF4BDC89840B84B3B0E737}

Voici les styles pour les contrôles du lecteur générique :

>[!TIP]
>
>Ces styles sont répertoriés dans le `default-controls.css` fichier.

<table id="table_0ACB6BAB5DAD42DBBD18CA7C0385A261"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-control</span> </td> 
   <td colname="col2"> <p>Applicable à tous les contrôles de la barre de contrôle à l'exception de la barre de défilement et de l'espace </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-input-slider</span> </td> 
   <td colname="col2"> <p>Curseurs d’entrée </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-header</span> </td> 
   <td colname="col2"> <p>En-tête des panneaux </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-vertical--menu-élément</span> </td> 
   <td colname="col2"> <p>de menu  dans un style vertical </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-fill-spacer</span> </td> 
   <td colname="col2"> <p>Espace sur la barre de contrôle </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-hr-separator</span> </td> 
   <td colname="col2"> <p>Séparateur de règle horizontal </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-title</span> </td> 
   <td colname="col2"> <p>Titre des panneaux </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-close-btn</span> </td> 
   <td colname="col2"> <p>Bouton de fermeture du panneau </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-button-Background</span> </td> 
   <td colname="col2"> <p>Arrière-plan de tous les boutons </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-txt-control</span> </td> 
   <td colname="col2"> <p>Styles par défaut des contrôles de texte. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Barre de contrôle {#section_B683B51EC746484B9AA90CB481D637BD}

Voici les styles de la barre de contrôle :

<table id="table_681E13F264674F849FAA2523EB65F094"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-control-bar</span> (comportement par défaut)</td>
   <td colname="col2"> <p>Applicable à la barre de contrôle </p> </td> 
  </tr> 
 </tbody> 
</table>

## Boutons Fonctionnalités {#section_57FFD242FF674EA2867BCF6CA7F6B855}

>[!NOTE]
>
>Les lettres des tableaux suivants correspondent aux lettres de cette illustration.

Voici les styles de la barre de défilement :

<table id="table_2207AD72E72A47FFA03AC748F06A54FD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style (A) </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar</span> </td> 
   <td colname="col2"> <p>Barre de défilement sur la barre de contrôle </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-buffer-progress-bar</span> </td> 
   <td colname="col2"> <p>Barre de progression de la mémoire tampon sur la barre de défilement </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-search-to-bar</span> </td> 
   <td colname="col2"> <p>Etat de la barre de défilement lorsque l’utilisateur effectue une recherche dessus </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-playback-progress-bar</span> </td> 
   <td colname="col2"> <p>État de la barre de défilement lors de la lecture normale </p> </td> 
  </tr>
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-progress-bar-play-head</span> </td>
   <td colname="col2"> <p>Lire la tête sur la barre de défilement pendant la lecture </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-ad-marqueur-bar</span> </td>
   <td colname="col2"> <p>Barre de marqueurs publicitaires </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-ad-marqueur</span> </td>
   <td colname="col2"> <p>Marque publicitaire </p> </td>
  </tr>
 </tbody>
</table>

Les comportements par défaut sont les suivants :

* `scrubBarBehavior`
* `bufferProgressBarBehavior`
* `playHeadBehavior`
* `playProgressBarBehavior`
* `seekToBarBehavior`

## Bouton Lecture/Pause {#section_F1F40A948D0049C5A4D8EA5F2A475CAA}

Voici les styles du bouton Lecture/Pause :

<table id="table_975C2293222A4782A8C75A6149C1AD27">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style (B) </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause</span> </td>
   <td colname="col2"> <p>Bouton Lecture en pause sur la barre de contrôle. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td>
   <td colname="col2"> <p><span class="codeph"> ptp-btn-playpause</span> dans l’état de mise en pause </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td> 
   <td colname="col2"> <p><span class="codeph"> ptp-btn-playpause</span> dans l’état de lecture </p> </td>
  </tr>
 </tbody>
</table>

Le comportement par défaut est `playPauseButtonBehavior`.

## Volume {#section_23E17BD2343948F8A2CEE1C8BEE2F874}

Voici les styles pour configurer le bouton de volume :

<table id="table_8F9831F36A4D427CA31C9FFA4173170D">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style (C) </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><span class="codeph"> .ptp-volume-control</span>
     <ul id="ul_B12ADDFB83EA40FD8B4E92AF418AA4B4">
      <li id="li_7DA8143A69ED4E7D8A560B9FF75D6BA7"><span class="codeph"> .expanded</span> </li>
      <li id="li_D8CCAD45D81C4850B6903FE261833AE6"><span class="codeph"> .vertical</span> </li>
     </ul> </p> </td>
   <td colname="col2"> <p>Contrôle du volume sur la barre de contrôle
     <ul id="ul_2C60F018FDCB458885738AC378C02F61">
      <li id="li_6B19572B504A4BBF9C97DC29C0E92A1D">Lorsque le contrôle est développé </li>
      <li id="li_6489E422E1944D5194CBDFC8383D2F30">Lorsque le contrôle est au format vertical </li>
     </ul> </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume</span> </td>
   <td colname="col2"> <p>Bouton Volume sur la barre de contrôle </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume.min-volume-état</span> </td>
   <td colname="col2"> <p>Lorsque le volume est à l'état minimal </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume.mute-state</span> </td>
   <td colname="col2"> <p>Lorsque le volume est à l'état muet </p> </td>
  </tr>
 </tbody>
</table>

Les comportements par défaut sont `volumeBehavior` et `muteButtonBehavior`.

Voici les styles du curseur de volume :

<table id="table_E3DC93F8FC614C30AADAE259D18F10EF">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style (D) </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-volume-slider</span> </td>
   <td colname="col2"> <p>Curseur de volume. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-volume-hidden</span> </td>
   <td colname="col2"> <p>Curseur de volume dans un état masqué. </p> </td>
  </tr>
 </tbody>
</table>

Le comportement par défaut est `volumeSliderBehavior`.

## Rembobiner {#section_06EE608FC54A4CF5B5DF9DC743CFC740}

Voici le style du bouton de rembobinage :

<table id="table_0ACB116582D54B188E9F5B5C03D3A615">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style (E) </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastrewind</span> </td>
   <td colname="col2"> <p>Bouton Rembobinage sur la barre de contrôle. </p> </td>
  </tr>
 </tbody>
</table>

Le comportement par défaut est `rewindButtonBehavior`.

## Heure {#section_0E6549B3DF6D4C10947D445A5F8EEA7F}

Voici le style pour afficher la durée restante sur la barre de contrôle :

<table id="table_CEE62BFF5FB04FDCBBE1331E0D727EBA">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style (F) </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-txt-display-time</span> </td>
   <td colname="col2"> <p>Affiche le temps restant sur la barre de contrôle </p> </td>
  </tr>
</tbody>
</table>

Le comportement par défaut est `timeRemainingBehavior`.

## Rembobinage rapide {#section_F6E6C65BD3BD493A89915DF9B92933BA}

Voici le style du bouton de rembobinage rapide :

<table id="table_25BB4966B709402383AB6A6822FC1999">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style (G) </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastrewind</span> </td>
   <td colname="col2"> <p>Bouton de rembobinage rapide sur la barre de contrôle. </p> </td>
  </tr>
 </tbody>
</table>

Le comportement par défaut est `fastRewindButtonBehavior`.

## Rembobinage lent {#section_38A22BB8681B430F8C6808C3BD21FB4E}

Voici le style du bouton de rembobinage lent :

<table id="table_E623C374622A497C91E22333D77AF8F6">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style (H) </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-ralenti</span> </td>
   <td colname="col2"> <p>Bouton de rembobinage lent sur la barre de contrôle. </p> </td>
  </tr>
 </tbody>
</table>

Le comportement par défaut est `slowRewindButtonBehavior`.

## En avant lent {#section_92ACF092EECC4A5EAF6AA090C05E552E}

Voici le style du bouton Avance lente :

<table id="table_88C1CF5DB2D84EDBA01AC62B70509B08">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style (I) </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-slow</span> </td>
   <td colname="col2"> <p>Bouton lent vers l’avant sur la barre de contrôle. </p> </td>
  </tr>
 </tbody>
</table>

Le comportement par défaut est `slowForwardButtonBehavior`.

## Avance rapide {#section_F90ED8B3739B49ACAB1F12DF18F0E4D6}

Voici le style du bouton Avance rapide :

<table id="table_F166BD1E8B934B34AF3690BBBAD894B7">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style (J) </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastforward</span> </td>
   <td colname="col2"> <p>Le bouton Avance rapide sur la barre de contrôle. </p> </td>
  </tr>
 </tbody>
</table>

Le comportement par défaut est `fastForwardButtonBehavior`.

## Piste audio {#section_1CDF4FA5A1C14DB6B9C96579FFA1057C}

Voici les styles pour configurer la piste audio :

<table id="table_22FC521D786B45EB84F230894FFECE79">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Bouton Piste Audio (K)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-audio-track</span> </td>
   <td colname="col2"> <p>Bouton de piste audio sur la barre de contrôle. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Le comportement par défaut est <span class="codeph"> audioTrackButtonBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Panneau de sélection des pistes audio (L)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-panel</span> </td> 
   <td colname="col2"> <p>Panneau de sélection de la piste audio. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Le comportement par défaut est <span class="codeph"> audioTrackSelectionPanelBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>En-tête de sélection de piste audio (M)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p>En-tête du panneau <span class="codeph"></span>ptp-audio-track-selection-panel. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Menu Sélection de piste audio (N)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-menu</span> </td>
   <td colname="col2"> <p>Les options de menu dans le panneau <span class="codeph"></span>ptp-audio-track-selection. </p> </td>
  </tr>
 </tbody>
</table>

## Partage {#section_B2ADC76E76304A68AD648A00A12B676E}

Voici les styles à configurer pour le partage :

<table id="table_3264C472809D462B8FC16680B96B1AC9">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Bouton de partage sur les réseaux sociaux (O)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video</span> </td> 
   <td colname="col2"> <p>Bouton de partage sur les réseaux sociaux sur la barre de contrôle qui ouvre le panneau <span class="codeph"></span>ptp-share-video. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Le comportement par défaut est <span class="codeph"> shareVideoButtonBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Partage du panneau vidéo (P)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel</span> </td>
   <td colname="col2"> <p>Panneau qui affiche les options de partage sur les réseaux sociaux. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Le comportement par défaut est <span class="codeph"> shareVideoPanelBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Menu Partage vidéo (Q)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p>En-tête du panneau <span class="codeph"></span>ptp-audio-track-selection-panel. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .share-video-panel-menu</span> </td>
   <td colname="col2"> <p>Menu du panneau <span class="codeph"></span> ptp-share-video-panelqui affiche toutes les options de partage de contenu sur les réseaux sociaux. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel-menu-item</span> </td>
   <td colname="col2"> <p>Elément de menu dans le menu <span class="codeph"></span>partagé-vidéo-panneau-vidéo. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-facebook</span> </td>
   <td colname="col2"> <p>Option de menu qui vous permet de partager du contenu sur Facebook. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-twitter</span> </td>
   <td colname="col2"> <p>Option de menu qui vous permet de partager du contenu sur Twitter. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-google-plus</span> </td>
   <td colname="col2"> <p>Elément de menu qui vous permet de partager du contenu sur Google Plus. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-linkedin</span> </td>
   <td colname="col2"> <p>Elément de menu qui vous permet de partager du contenu sur LinkedIn. </p> </td>
  </tr>
 </tbody>
</table>

## Sous-titres {#section_A01BA68218564DA0B7D6BF51F045D7AB}

Voici les styles pour configurer les sous-titres :

<table id="table_777C7034C9424F8C841DABD480FFAC47">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Style </th>
   <th colname="col2" class="entry"> Description </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Bouton Légendes fermées (R)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-close-caption</span> </td>
   <td colname="col2"> <p>Bouton <span class="uicontrol"> Sous-titres</span> de la barre de contrôle. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Le comportement par défaut est <span class="codeph"> closeCaptionButtonBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .on-state</span> </td>
   <td colname="col2"> <p>Les légendes ont été activées pour une vidéo. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Panneau Sous-Titres (S)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-panel</span> </td>
   <td colname="col2"> <p>Panneau des sous-titres. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Le comportement par défaut est <span class="codeph"> closeCaptionLanguagePanelBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Langues des sous-titres (T)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-language-panel :</span> </td>
   <td colname="col2"> <p>En-tête du panneau <span class="codeph"></span>ptp-audio-track-selection-panel. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-language-menu: </span> </td>
   <td colname="col2"> <p>Menu dans le panneau des sous-titres. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Options des sous-titres (U)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-options-btn</span> </td>
   <td colname="col2"> <p>Le bouton <span class="uicontrol"> Options</span> du panneau d’options des sous-titres. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-options-panel</span> </td>
   <td colname="col2"> <p>Panneau Options du panneau sous-titres fermé. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-menu-item</span> </td>
   <td colname="col2"> <p>Elément de menu du panneau sous-titres. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .selected</span> </td>
   <td colname="col2"> <p>Dans l’état sélectionné. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-close-caption-done-btn</span> </td> 
   <td colname="col2"> <p>Le bouton <span class="uicontrol"> Terminé</span> dans l’en-tête du panneau d’options des sous-titres. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-close-caption-options-menu</span> </td> 
   <td colname="col2"> <p>Le menu Options dans les sous-titres. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-main-menu</span> </td> 
   <td colname="col2"> <p>Menu principal des options de sous-titrage. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-sous-menu</span> </td> 
   <td colname="col2"> <p>Sous-menu des options de sous-titrage. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-opacity-slider</span> </td> 
   <td colname="col2"> <p>Curseur d’opacité pour les options de sous-titrage codé. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-menu-séparateur</span> </td> 
   <td colname="col2"> <p>Séparateur d’options de sous-titrage fermé. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-menu-item</span> </td> 
   <td colname="col2"> <p>Option <span class="uicontrol"> de menu Options</span> de sous-titrage. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption--panel</span> </td> 
   <td colname="col2"> <p>Panneau  sous-titrage fermé. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-pied de page</span> </td> 
   <td colname="col2"> <p>Pied de page des options de sous-titrage. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-reset-button</span> </td> 
   <td colname="col2"> <p>Le bouton <span class="uicontrol"> Réinitialiser</span> dans le pied de page du panneau d’options de sous-titrage fermé. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-close-caption-options-appliquer-bouton</span> </td> 
   <td colname="col2"> <p>Le bouton <span class="uicontrol"> Appliquer</span> dans le pied de page du panneau d’options de sous-titrage fermé. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Le comportement par défaut est <span class="codeph"> closeCaptionOptionsPanelBehavior</span>. </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## Autres options (V) {#section_18E25CF8A8964FFD9026A8A833089CE3}

Voici les styles pour configurer d’autres options :
<table id="table_EC6EF88E2EDE4B8EBB1C14F87A6161FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-plus-options</span> </td> 
   <td colname="col2"> <p>Le bouton <span class="uicontrol"> Plus d’options</span> . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-plus-options.ptp-contrôle-bar-btn</span> </td> 
   <td colname="col2"> <p>ptp-btn-more-options <span class="codeph"></span> utilisées dans la barre de contrôle. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-plus-options-contrôle-panneau</span> </td> 
   <td colname="col2"> <p>Panneau de configuration Plus d’options. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-plus-options-contrôle-panneau-menu</span> </td> 
   <td colname="col2"> <p>Le menu du panneau de contrôle Plus d’options. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-plus-options-contrôle-panneau-menu-élément</span> </td> 
   <td colname="col2"> <p>Option de menu du panneau de contrôle Plus d’options. </p> </td> 
  </tr> 
 </tbody> 
</table>

Le comportement par défaut est `moreOptionsButtonBehavior`.

## Bouton PIP (W) {#section_1EE039DEA99541D391B30BD1DF72A83E}

Voici le style du [!UICONTROL PIP<] bouton :

<table id="table_EE2E882C87E24D39B8D5347686F29E55"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-pip</span> </td> 
   <td colname="col2"> <p>Bouton PIP sur la barre de contrôle. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Le comportement par défaut est <span class="codeph"> pipButtonBehavior</span>. </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## Plein écran (X) {#section_158A19DFB30E4432A67E4A74A7CBA563}

Voici le style de configuration du plein écran :

<table id="table_5941835F31AC4E9CBA9702AB8D813B8F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-fullscreen</span> </td> 
   <td colname="col2"> <p>Le bouton <span class="uicontrol"> Plein écran</span> de la barre de contrôle. </p> </td> 
  </tr> 
 </tbody> 
</table>

Le comportement par défaut est `fullScreenButtonBehavior`.

## Lecture par erreur (Y) {#section_AE6F83BB7EE2497FB13CD94A8316192D}

Voici le style pour configurer le jeu de astuces :

<table id="table_F1ADAC0A4B4E48669828690BDEB4BC09"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-control-bar-trick-play-rate</span> </td> 
   <td colname="col2"> <p>Composant d'affichage de taux de ruse dans la barre de contrôle. </p> </td> 
  </tr> 
 </tbody> 
</table>

Le comportement par défaut est `trickPlayRateDisplayBehavior`.

## Multivue (Z) {#section_58EFAE7263BA45D3A4E2AB7309A9CAA7}

Voici le style de configuration de la vue multiple :

<table id="table_84B37D7410EE40DFA7A8BB8431C6DCF0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-multiview</span> </td> 
   <td colname="col2"> <p>Le bouton <span class="uicontrol"> MultiView</span> sur la barre de contrôle et l’état initial du bouton <span class="uicontrol"> Multiview</span> . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Le comportement par défaut est <span class="codeph"> multiViewButtonBehavior</span>. </td> 
   <td colname="col2"> </td> 
  </tr> 
 </tbody> 
</table>

## Miniature {#section_0AFD932975634BB08387EEE7D3BFC438}

Voici le style de configuration des miniatures :

<table id="table_968136A8BBA042A7A8E79739B8F92F55"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-progress-bar-pouce-clou</span> </td> 
   <td colname="col2"> <p>Barre de progression des miniatures. </p> </td> 
  </tr> 
 </tbody> 
</table>

Le comportement par défaut est `thumbnailPreviewBehavior`.

## Messages d’erreur {#section_AC9858EE1B5A4FF4947E383C663B6AB5}

Voici le style de configuration des messages d’erreur :

<table id="table_7F4C156170DB4AFFA7DEE06F00449506"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel</span> </td> 
   <td colname="col2"> <p>Panneau qui affiche les messages d’erreur du lecteur. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panneau-icône</span> </td> 
   <td colname="col2"> <p>Icône affichée dans le panneau en cas de message d’erreur. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panneau-message</span> </td> 
   <td colname="col2"> <p>Message d’erreur affiché. </p> </td> 
  </tr> 
 </tbody> 
</table>

Le comportement par défaut est `errorMessagePanelBehavior`.

## Recouvrement de la mémoire tampon {#section_2FE8FDE2599E42BAA7411D0D38FA0A88}

Voici le style de configuration des miniatures :

<table id="table_1FECE1DC29B8434B886751A29455F004"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-buffering-overlay</span> </td> 
   <td colname="col2"> <p>Commande d’incrustation de mise en mémoire tampon. </p> </td> 
  </tr> 
 </tbody> 
</table>

L’incrustation par défaut est `bufferingOverlayBehavior`.

## Sélecteurs spécifiques {#section_51F735AEF82E41E890FF59E031A0DB89}

Voici le style du bouton Avance rapide :

<table id="table_E77EDC7D227348E79C7E73FB5D46F992"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Style </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ad-break</span> </td> 
   <td colname="col2"> <p>Etat du panneau de contrôle pendant la lecture de la publicité. </p> <p>S’applique aux éléments suivants : 
     <ul id="ul_D5076303DCD94D968682289823D1A9F2"> 
      <li id="li_4290C4B2D48546E3AD023BED6CAAE395"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_72A3D3E916E44A55BA170407EAB0527D"><span class="codeph"> .ptp-btn-fastrewind</span> </li> 
      <li id="li_A0BAEBB0E01B402EB83E3CE9B92B15CC"><span class="codeph"> .ptp-btn-fastrewind</span> </li> 
      <li id="li_FDF2CEDB0A854098907FF9CBCF1A61C1"><span class="codeph"> .ptp-btn-slow</span> </li> 
      <li id="li_CD2E14DB3DD64C10A253DA23FBE04A04"><span class="codeph"> .ptp-btn-slow</span> </li> 
      <li id="li_A230359E8F7F4571A9EBFF0E4C2462D7"><span class="codeph"> .ptp-btn-ralenti</span> </li> 
      <li id="li_5711A315872F4FA59FDDF0EF0AFD03C6"><span class="codeph"> .ptp-btn-plus-options </span> </li> 
      <li id="li_71C8E76077A84ED590160AB5ABFCC0D7"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_4A3113C0360F4F708AAA96AB316FA057"><span class="codeph"> .ptp-btn-close-caption </span> </li> 
      <li id="li_901A0186D65A48A1B774DC555CEC5367"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
      <li id="li_2331583C01C2482B8EE72979FBF111DB"><span class="codeph"> .ptp-btn-pip </span> </li> 
      <li id="li_7BB39BDF5E294AEB8FA3DCD9F9A29468"><span class="codeph"> .ptp-btn-rewind</span> </li> 
      <li id="li_E4FEF5A7486A40F6A5FE1119BD63AFEF"><span class="codeph"> .ptp-scrub-bar</span> </li> 
      <li id="li_12153547558A4871842EE0416BCCA8B2"><span class="codeph"> .ptp-Recherche-vers-barre</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multi-</span> </td> 
   <td colname="col2"> <p>Etat du contrôle lors de la consultation multiple. </p> <p>S’applique aux éléments suivants : 
     <ul id="ul_A8AC653C30814AC49041F3B58A2106F4"> 
      <li id="li_0407167DA21647A8A6960DFE55A33F42"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_EA71CAF41CDC41DE859A85CE482BE97C"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_F3A998C51A034C22A914EAEFF19FFEA7"><span class="codeph"> .ptp-btn-close-caption</span> </li> 
      <li id="li_022F871ABC894C9BA879B3AF3D341202"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .fullscreen-state</span> </td> 
   <td colname="col2"> <p>Le lecteur est en mode plein écran. </p> <p>S’applique aux éléments suivants : 
     <ul id="ul_B235C1D339F64B2FAC6BC72F03807616"> 
      <li id="li_6E050EE74C604FDAB4C9C0447F547A9D"><span class="codeph"> .ptp-control-bar </span> </li> 
      <li id="li_67D54B1A41764B2DA544479CDA1C901C"><span class="codeph"> .ptp-btn-fullscreen</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>