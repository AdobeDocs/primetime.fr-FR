---
description: Ces classes fournissent des informations sur les publicités qui se produisent dans une chronologie.
title: Classes publicitaires de journal
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Classes publicitaires de journal {#timeline-advertising-classes}

Ces classes fournissent des informations sur les publicités qui se produisent dans une chronologie.

<table frame="all" colsep="1" rowsep="1" id="table_1A59E777BA99466793D586286F19E933"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Nom</b></th> 
   <th colname="2" class="entry"><b>Description</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAd.html" format="html" scope="external"> PTAd</a> </td> 
   <td colname="2">Classe qui définit l’abstraction de la publicité et contient toutes les informations sur la publicité. Elle est définie par un identifiant unique, une durée et une ressource MediaResource. MediaResource contient l’URL où réside le contenu publicitaire réel. 
    <pre>
      Représente une ressource linéaire principale épissée dans le contenu. Il peut éventuellement contenir un tableau de ressources compagnons qui doit être affiché avec la ressource linéaire.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdAsset.html" format="html" scope="external"> PTAdAsset</a> </td> 
   <td colname="2">Classe qui représente une ressource à afficher. 
    <pre>
      Représente une ressource à afficher.
    </pre> 
    <pre>
      Classe représentant une ressource publicitaire.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBannerView.html" format="html" scope="external"> PTAdBannerView</a> </td> 
   <td colname="2">
    <pre>
      Affiche une ressource de bannière. Votre application doit créer une instance de cette classe d’utilitaire, définir la ressource de bannière et l’ajouter à une vue. Le suivi des impressions et des clics pour la bannière est géré en interne par cette classe.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBreak.html" format="html" scope="external"> PTAdBreak</a> </td> 
   <td colname="2">Classe qui offre une vue unifiée sur plusieurs publicités qui seront lues à un moment donné pendant la lecture. 
    <pre>
      Représente une séquence continue de publicités épissées dans le contenu.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdClick.html" format="html" scope="external"> PTAdClick</a> </td> 
   <td colname="2">Classe qui représente une instance de clic associée à une ressource. Cette instance contient des informations sur l’URL du clic publicitaire et le titre qui peuvent être utilisés pour fournir des informations supplémentaires à l’utilisateur. 
    <pre>
      Représente une instance de clic associée à une ressource. Cette instance contient des informations sur l’URL du clic publicitaire et le titre qui peuvent être utilisés pour fournir des informations supplémentaires à l’utilisateur.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdPolicyInfo.html" format="html" scope="external"> PTAdPolicyInfo</a> </td> 
   <td colname="2"> Protocole qui définit les propriétés des appels de l’API AdPolicySelector. Ces propriétés fournissent le contexte pour appliquer chaque comportement publicitaire. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTAdPolicySelector.html" format="html" scope="external">PTAdPolicySelector</a></td> 
   <td colname="2"> Protocole du sélecteur de stratégie publicitaire pour appliquer les comportements publicitaires. Les applications peuvent se conformer à ce protocole en implémentant toutes les méthodes requises ou en étendant la classe de sélecteur de stratégie par défaut existante pour personnaliser des comportements spécifiques. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdTimeline.html" format="html" scope="external">PTAdTimeline</a></td> 
   <td colname="2"> Classe qui représente la chronologie des sauts dans le contenu. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 
    <pre>
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTContentResolver.html" format="html" scope="external"> PTContentResolver</a> Classe, 
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolver.html" format="html" scope="external"> PTContentResolver</a> protocol
    </pre> </td> 
   <td colname="2"> Classe qui gère la partie de résolution des publicités dans le processus de prise de décision publicitaire Adobe Primetime. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolverDelegate.html" format="html" scope="external"> PTContentResolverDelegate</a> </td> 
   <td colname="2"> Protocole qui décrit les méthodes du programme de résolution de contenu personnalisé ( <span class="codeph"> PTContentResolver</span> ) doit utiliser pour communiquer au délégué l’état de la résolution du contenu. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Constants/PTPlacementType.html" format="html" scope="external"> PTPlacementType</a> </td> 
   <td colname="2">Classe qui extrait une demande d’informations d’emplacement. Chaque publicité résolue doit comporter une information d’emplacement qui lui est associée. Les informations d’emplacement décrivent l’emplacement de la publicité qui doit être placée dans la chronologie. Il contient des informations telles que : 
    <ul id="ul_A9105A78F0C24488BCD5E3F2EE62A3EE"> 
     <li id="li_01E968A4330D4B40BA1EB6F4A6000FFD">Position de l’emplacement (en ms) </li> 
     <li id="li_A3DC9498BEE14FBA9E7A5D26874F3984">Type de l’emplacement (preroll, mid-roll ou post-roll) </li> 
     <li id="li_4B9094DD318B4792854A377CC6064232">Durée du bloc de contenu principal sur le point d’être remplacé </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
