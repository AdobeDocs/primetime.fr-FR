---
description: Ces classes décrivent votre lecteur multimédia et ses ressources.
title: Classes du lecteur multimédia
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# Classes du lecteur multimédia {#media-player-classes}

Vous pouvez utiliser l’API Objective-C du lecteur Primetime pour personnaliser le comportement du lecteur.

Ces classes décrivent votre lecteur multimédia et ses ressources.

<table frame="all" colsep="1" rowsep="1" id="table_bm2_wl2_2m"> 
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>Classe</b> </td> 
   <td colname="2"><b>Description</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTABRControlParameters.html" format="html" scope="external"> PTABRControlParameters</a></span> </td> 
   <td colname="2">Encapsule tous les paramètres de contrôle de débit adaptatif. Les paramètres pris en charge sont les suivants : 
    <ul id="ul_pnh_hm2_2m"> 
     <li id="li_46572FE1EB514AFF8C9F731E44DAF30B"><span class="codeph"> minBitRate</span> </li> 
     <li id="li_A10C75C9A5234241A5B84A4139F4D143"><span class="codeph"> maxBitRate</span> </li> 
     <li id="li_4E77E367A2E848D2B3E1A9C52209A7B2"><span class="codeph"> initialBitRate</span> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTDefaultMediaPlayerClientFactory.html" format="html" scope="external"> PTDefaultMediaPlayerClientFactory</a></span> </td> 
   <td colname="2"> Implémentation par défaut de <span class="codeph"> PTMediaPlayerClientFactory</span> dans TVSDK. Il fournit les <span class="codeph"> PTOpportunityResolver</span>, <span class="codeph"> PTContentResolver</span>, et <span class="codeph"> PTAdPolicySelector</span> instances. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html" format="html" scope="external"> PTMediaPlayer</a></span> </td> 
   <td colname="2">Définit le composant racine de la structure du lecteur Primetime. <p>Les applications créent une instance de cette classe pour lire un média. Ce composant envoie des notifications pour informer votre application du statut du lecteur à un moment donné. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTMediaPlayerClientFactory.html" format="html" scope="external"> PTMediaPlayerClientFactory</a></span> </td> 
   <td colname="2"> Protocole qui décrit les méthodes qu’une fabrique de clients de lecteurs multimédia personnalisés doit mettre en oeuvre pour fournir les <span class="codeph"> PTOpportunityResolver</span> , <span class="codeph"> PTContentResolver</span> et <span class="codeph"> PTAdPolicySelector</span> instances. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerItem.html" format="html" scope="external"> PTMediaPlayerItem</a></span> </td> 
   <td colname="2"> Représente un média audio-vidéo spécifique. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerView.html" format="html" scope="external"> PTMediaPlayerView</a></span> </td> 
   <td colname="2"> Gère le composant d’affichage de la structure du lecteur Primetime. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaProfile.html" format="html" scope="external"> PTMediaProfile</a></span> </td> 
   <td colname="2"> Représente le profil d’un seul flux dans la liste de lecture des variantes. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaSelectionOption.html" format="html" scope="external"> PTMediaSelectionOption</a></span> </td> 
   <td colname="2">Représente une ressource multimédia audiovisuelle afin de prendre en compte différentes préférences linguistiques, exigences d’accessibilité ou configurations d’application personnalisées. Types d’option valides : 
    <ul id="ul_p2q_gn2_2m"> 
     <li id="li_46BE5AE49732481FB6D336FFF896E5AD">Sous-titres (<span class="codeph"> PTMediaSelectionOptionTypeSubtitle</span>) </li> 
     <li id="li_6CEADCA12D4A48B7AE4A539985F32119">Autre son (<span class="codeph"> PTMediaSelectionOptionTypeAudio</span>) </li> 
     <li id="li_248D3D997F8A4B6E9B48869F84060D1F"> <p>Non définie (<span class="codeph"> PTMediaSelectionOptionTypeUndefined</span>) </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTOpportunityResolver.html" format="html" scope="external"> PTOpportunityResolver</a> </span> Classe, <span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTOpportunityResolver.html" format="html" scope="external"> PTOpportunityResolver</a> protocol</span> </td> 
   <td colname="2"> Classe utilisée pour le traitement de signaux in-manifest qui seront utilisés comme emplacements pour le processus de prise de décision publicitaire Adobe Primetime. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTOpportunityResolverDelegate.html" format="html" scope="external"> PTOpportunityResolverDelegate</a></span> </td> 
   <td colname="2"> Protocole qui décrit les méthodes du programme de résolution d’opportunités personnalisé ( <span class="codeph"> PTOpportunityResolver</span> ) doit utiliser pour communiquer au délégué le statut de la résolution de l’opportunité. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTSDK.html" format="html" scope="external"> PTSDK</a></span> </td> 
   <td colname="2"> Décrit la version de TVSDK et ses fonctionnalités. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTSDKConfig.html" format="html" scope="external"> PTSDKConfig</a></span> </td> 
   <td colname="2"> Expose les paramètres globaux TVSDK et permet à une application de s’abonner à des balises HLS personnalisées. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTTextStyleRule.html" format="html" scope="external"> PTTextStyleRule</a></span> </td> 
   <td colname="2"> Définit des constantes qui représentent les clés d’attribut de style texte qui forment le dictionnaire des règles. </td> 
  </tr> 
 </tbody> 
</table>
