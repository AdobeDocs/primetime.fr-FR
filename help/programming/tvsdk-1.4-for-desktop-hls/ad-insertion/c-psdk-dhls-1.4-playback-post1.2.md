---
description: Le comportement de la lecture multimédia est affecté par la recherche, la mise en pause, l’avance rapide ou le rembobinage (mode de lecture de l’astuce) et l’inclusion de la publicité.
seo-description: Le comportement de la lecture multimédia est affecté par la recherche, la mise en pause, l’avance rapide ou le rembobinage (mode de lecture de l’astuce) et l’inclusion de la publicité.
seo-title: Comportement de lecture par défaut et personnalisé avec les publicités
title: Comportement de lecture par défaut et personnalisé avec les publicités
uuid: 45e6b0cd-fb0b-4896-b53a-d3bd78a3c1f3
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Comportement de lecture par défaut et personnalisé avec les publicités{#default-and-customized-playback-behavior-with-ads}

Le comportement de la lecture multimédia est affecté par la recherche, la mise en pause, l’avance rapide ou le rembobinage (mode de lecture de l’astuce) et l’inclusion de la publicité.

Pour remplacer le comportement par défaut, utilisez `AdPolicySelector`.

>[!IMPORTANT]
>
>TVSDK ne permet pas de désactiver la recherche pendant les publicités. Adobe recommande de configurer votre application pour désactiver la recherche pendant les publicités.

Le tableau suivant décrit comment TVSDK gère les publicités et les coupures publicitaires pendant la lecture :

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> activité vidéo </th> 
   <th colname="col2" class="entry"> Stratégie de comportement TVSDK par défaut </th> 
   <th colname="col3" class="entry">Personnalisation disponible via <span class="codeph"> AdPolicySelector</span> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Pendant la lecture normale, une coupure publicitaire est rencontrée. </td> 
   <td colname="col2"> 
    <ul id="ul_10D2638676EA4ADDA718E61BD4FDC1D2"> 
     <li id="li_D5CC30F063934C738971E2E8AF00C137"> Dans le cas d’une coupure de publicité en direct ou linéaire, la coupure de publicité est lue, même si elle a déjà été visionnée. </li> 
     <li id="li_D962C0938DA74186AE99D117E5A74E38">Pour VOD, lit la coupure publicitaire et la marque comme visionnée. </li> 
    </ul> </td> 
   <td colname="col3">Spécifiez une autre stratégie pour la coupure publicitaire à l’aide de <span class="codeph"> selectPolicyForAdBreak</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche sur les coupures publicitaires dans le contenu principal. </td> 
   <td colname="col2"> Lit la dernière coupure publicitaire non visionnée qui a été ignorée et reprend la lecture à la position de recherche souhaitée lorsque la coupure est terminée. </td> 
   <td colname="col3">Sélectionnez le saut de pause à lire en <span class="codeph"> sélectionnant AdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche en amont sur les coupures publicitaires dans le contenu principal. </td> 
   <td colname="col2"> Ignore la position de recherche souhaitée sans lire les coupures publicitaires. </td> 
   <td colname="col3">Sélectionnez le saut de pause à lire en <span class="codeph"> sélectionnant AdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche dans une coupure publicitaire. </td> 
   <td colname="col2"> Lit à partir du début de la publicité au cours de laquelle la recherche s’est terminée. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire et pour la publicité spécifique où la recherche s'est terminée à l'aide de <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche en amont dans une coupure publicitaire. </td> 
   <td colname="col2"> Lit à partir du début de la publicité au cours de laquelle la recherche s’est terminée. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire et pour la publicité spécifique dans laquelle la recherche s'est terminée à l'aide de <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant ou vers l’arrière sur les coupures publicitaires surveillées dans le contenu principal. </td> 
   <td colname="col2"> Si la dernière coupure publicitaire ignorée a déjà été visionnée, passe à la position de recherche sélectionnée par l’utilisateur. </td> 
   <td colname="col3">Sélectionnez les pauses sautées à lire en <span class="codeph"> sélectionnant AdBreaksToPlay</span> et déterminez celles qui ont déjà été visionnées en utilisant <span class="codeph"> TimeLineItem.watched</span> . <p>Important :  Par défaut, TVSDK marque une coupure publicitaire comme visionnée immédiatement après avoir saisi la première publicité de la coupure publicitaire. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant ou vers l’arrière sur un ou plusieurs coupures publicitaires et passe à une coupure publicitaire surveillée. </td> 
   <td colname="col2"> Ignore la coupure publicitaire et recherche la position immédiatement après la coupure publicitaire. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire (avec l’état de contrôle défini sur true) et pour la publicité spécifique où la recherche s’est terminée à l’aide de <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application entre dans le mode "trick-play" (mode DVR). Le taux de lecture peut être négatif (rembobinage) ou supérieur à 1 (avance rapide). </td> 
   <td colname="col2"> Ignore toutes les publicités lors d’une avance rapide ou d’un retour arrière, lit la dernière coupure sautée après la fin de la lecture de l’astuce et passe à la position de lecture de l’astuce sélectionnée par l’utilisateur lorsque cette coupure termine la lecture. </td> 
   <td colname="col3">Sélectionnez l’une des pauses sautées à lire après la fin de la lecture de l’astuce à l’aide de <span class="codeph"> la sélection de AdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant sur les publicités insérées à l’aide de marqueurs publicitaires personnalisés. </td> 
   <td colname="col2"> Ignore la position de recherche sélectionnée par l’utilisateur. </td> 
   <td colname="col3">Pour plus d’informations, voir <a href="../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-ui-configure/t-psdk-dhls-1.4-ui-seek-scrub-bar-display.md" format="dita" scope="local"> Affichage d’une barre de défilement de recherche avec la position de lecture actuelle...</a> </td> 
  </tr> 
 </tbody> 
</table>

