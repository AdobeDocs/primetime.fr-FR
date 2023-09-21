---
description: Le comportement de la lecture multimédia est affecté par la recherche, la mise en pause, l’avance rapide ou le retour arrière (mode de lecture de l’astuce) et l’inclusion de la publicité.
title: Comportement de lecture par défaut et personnalisé avec les publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# Comportement de lecture par défaut et personnalisé avec les publicités {#default-and-customized-playback-behavior-with-ads}

Le comportement de la lecture multimédia est affecté par la recherche, la mise en pause, l’avance rapide ou le retour arrière (mode de lecture de l’astuce) et l’inclusion de la publicité.

Pour remplacer le comportement par défaut, utilisez `AdBreakPolicySelector`.

>[!IMPORTANT]
>
>TVSDK ne permet pas de désactiver la recherche pendant les publicités. Adobe recommande de configurer votre application pour désactiver la recherche pendant les publicités.

Voici le comportement de lecture pour le contenu en direct/linéaire :

* La reprise de la lecture après une mise en pause entraîne la lecture du contenu qui a été mis en mémoire tampon au moment de la mise en pause.

  Si la position de reprise est toujours dans la plage de lecture, la lecture doit être continue. Sinon, TVSDK passe au nouveau point d’entrée. Vous pouvez également effectuer une opération de recherche et sélectionner un autre point de lecture.
* TVSDK résout les publicités entre les signaux après la position à laquelle l’application entre en lecture en direct.

  La lecture commence une fois la première repère résolue. La valeur par défaut pour la saisie de la lecture en direct est le point d’entrée client, mais vous pouvez choisir une autre position. Tous les signaux avant la position initiale sont résolus une fois que l’application a effectué une recherche dans la fenêtre de l’enregistreur numérique (DVR).

Le tableau suivant décrit comment TVSDK gère les publicités et les coupures publicitaires pendant la lecture :

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Activité vidéo </th> 
   <th colname="col2" class="entry"> Stratégie de comportement TVSDK par défaut </th> 
   <th colname="col3" class="entry">Personnalisation disponible via <span class="codeph"> AdBreakPolicySelector </span> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Lors de la lecture normale, une coupure publicitaire se produit. </td> 
   <td colname="col2"> 
    <ul id="ul_10D2638676EA4ADDA718E61BD4FDC1D2"> 
     <li id="li_D5CC30F063934C738971E2E8AF00C137"> Pour la lecture directe/linéaire, lit la coupure publicitaire, même si la coupure publicitaire a déjà été visionnée. </li> 
     <li id="li_D962C0938DA74186AE99D117E5A74E38">Pour VOD, lit la coupure publicitaire et marque la coupure publicitaire comme visionnée. </li> 
    </ul> </td> 
   <td colname="col3">Spécifiez une autre stratégie pour la coupure publicitaire à l’aide de <span class="codeph"> selectPolicyForAdBreak</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche au-dessus de la ou des coupures publicitaires dans le contenu principal. </td> 
   <td colname="col2"> Lit la dernière coupure publicitaire non visionnée qui a été sautée et reprend la lecture à la position de recherche souhaitée lorsque la coupure est terminée. </td> 
   <td colname="col3">Sélectionnez la coupure ignorée à lire à l’aide de <span class="codeph"> selectAdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’arrière par rapport aux coupures publicitaires dans le contenu principal. </td> 
   <td colname="col2"> Ignore la position de recherche souhaitée sans lire les coupures publicitaires. </td> 
   <td colname="col3">Sélectionnez la coupure ignorée à lire à l’aide de <span class="codeph"> selectAdBreaksToPlay</span>.                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche dans une coupure publicitaire. </td> 
   <td colname="col2"> Lit à partir du début de la publicité dans laquelle la recherche s’est terminée. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire et pour la publicité spécifique où la recherche s’est terminée à l’aide de <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’arrière dans une coupure publicitaire. </td> 
   <td colname="col2"> Lit à partir du début de la publicité dans laquelle la recherche s’est terminée. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire et pour la publicité spécifique dans laquelle la recherche s’est terminée en utilisant <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant ou vers l’arrière sur les coupures publicitaires visionnées dans le contenu principal. </td> 
   <td colname="col2"> Si la dernière coupure publicitaire ignorée a déjà été visionnée, passe à la position de recherche sélectionnée par l’utilisateur. </td> 
   <td colname="col3">Sélectionnez les pauses ignorées à l’aide de <span class="codeph"> selectAdBreaksToPlay</span> et déterminer les coupures qui ont déjà été visionnées à l’aide de <span class="codeph"> AdBreak.isWatched</span>. <p>Important : Par défaut, TVSDK marque une coupure publicitaire comme vue immédiatement après la première publicité dans la coupure publicitaire. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant ou vers l’arrière sur une ou plusieurs coupures publicitaires et passe à une coupure publicitaire surveillée. </td> 
   <td colname="col2"> Ignore la coupure publicitaire et recherche la position immédiatement après la coupure publicitaire. </td> 
   <td colname="col3">Spécifiez une autre stratégie publicitaire pour la coupure publicitaire (avec l’état de contrôle défini sur true) et pour la publicité spécifique où la recherche s’est terminée à l’aide de <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application entre dans le mode de lecture par astuces (mode DVR). Le taux de lecture peut être négatif (retour arrière) ou supérieur à 1 (avance rapide). </td> 
   <td colname="col2"> Ignore toutes les publicités lors d’un revirement ou d’un revirement rapide, lit la dernière coupure ignorée après la fin de la lecture de l’astuce et ignore la position de lecture de l’utilisateur sélectionnée lorsque cette coupure termine la lecture. </td> 
   <td colname="col3">Sélectionnez la ou les coupures ignorées à lire une fois la lecture de l’astuce terminée à l’aide de <span class="codeph"> selectAdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Votre application effectue une recherche vers l’avant par rapport aux publicités qui ont été insérées à l’aide de marqueurs publicitaires personnalisés. </td> 
   <td colname="col2"> Ignore la position de recherche sélectionnée par l’utilisateur. </td> 
   <td colname="col3">Pour plus d’informations, voir <a href="../../tvsdk-1.4-for-android/ui-configure/android-1.4-ui-seek-scrub-bar-display.md">Afficher une barre de défilement de recherche avec la position de lecture actuelle</a>. </td> 
  </tr> 
 </tbody> 
</table>
