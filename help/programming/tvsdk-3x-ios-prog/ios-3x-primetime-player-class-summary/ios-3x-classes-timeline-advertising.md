---
description: Ces classes fournissent des informations sur les publicités qui surviennent dans un plan de montage chronologique.
seo-description: Ces classes fournissent des informations sur les publicités qui surviennent dans un plan de montage chronologique.
seo-title: Classes publicitaires de la chronologie
title: Classes publicitaires de la chronologie
uuid: df970e8f-4bf8-4367-9d70-42ebcb11c025
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---


# Classes publicitaires de la chronologie {#timeline-advertising-classes}

Ces classes fournissent des informations sur les publicités qui surviennent dans un plan de montage chronologique.

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
   <td colname="2">Classe qui définit l’abstraction de la publicité et contient toutes les informations sur la publicité. Il est défini par un identifiant unique, une durée et une ressource MediaResource. MediaResource contient l’URL où réside le contenu publicitaire réel. 
    <pre>
      Représente un actif linéaire Principal épissé dans le contenu. Il peut éventuellement contenir un tableau de ressources complémentaires qui doivent être affichées avec la ressource linéaire.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdAsset.html" format="html" scope="external"> PTAdAsset</a> </td> 
   <td colname="2">Classe qui représente une ressource à afficher. 
    <pre>
      Représente un fichier à afficher.
    </pre> 
    <pre>
      Classe représentant une ressource publicitaire.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBannerView.html" format="html" scope="external"> PTAdBannerView</a> </td> 
   <td colname="2">
    <pre>
      Affiche un fichier de bannière. Votre application doit créer une nouvelle instance de cette classe d'utilitaires, définir le fichier de bannière et l'ajouter à une vue. Le suivi des impressions et des clics pour la bannière est géré en interne par cette classe.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBreak.html" format="html" scope="external"> PTAdBreak</a> </td> 
   <td colname="2">Classe qui donne une vue unifiée sur plusieurs publicités qui seront lues à un moment donné pendant la lecture. 
    <pre>
      Représente une séquence continue de publicités épissées dans le contenu.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdClick.html" format="html" scope="external"> PTAdClick</a> </td> 
   <td colname="2">Classe qui représente une instance de clic associée à une ressource. Cette instance contient des informations sur l’URL de clic publicitaire et le titre qui peuvent être utilisés pour fournir des informations supplémentaires à l’utilisateur. 
    <pre>
      Représente une instance de clic associée à une ressource. Cette instance contient des informations sur l’URL de clic publicitaire et le titre qui peuvent être utilisés pour fournir des informations supplémentaires à l’utilisateur.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdPolicyInfo.html" format="html" scope="external"> PTAdPolicyInfo</a> </td> 
   <td colname="2"> Protocole qui définit les propriétés des appels d’API AdPolicySelector. Ces propriétés fournissent le contexte pour appliquer chaque comportement publicitaire. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTAdPolicySelector.html" format="html" scope="external">PTAdPolicySelector</a></td> 
   <td colname="2"> Protocole de sélecteur de stratégies publicitaires pour l'application des comportements publicitaires. Les applications peuvent se conformer à ce protocole en implémentant toutes les méthodes requises ou en étendant la classe de sélecteur de stratégies par défaut existante pour personnaliser des comportements spécifiques. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdTimeline.html" format="html" scope="external">PTAdTimeline</a></td> 
   <td colname="2"> Classe qui représente la chronologie des sauts dans le contenu. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 
    <pre>
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTContentResolver.html" format="html" scope="external"> </a> PTContentResolverclass,  
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolver.html" format="html" scope="external"> </a> PTContentResolverprotocol
    </pre> </td> 
   <td colname="2"> Classe qui gère la partie de résolution des publicités dans le processus de prise de décision des publicités Adobe Primetime. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolverDelegate.html" format="html" scope="external"> PTContentResolverDelegate</a> </td> 
   <td colname="2"> Protocole décrivant les méthodes que le résolveur de contenu personnalisé ( <span class="codeph"> PTContentResolver</span> ) doit utiliser pour communiquer au délégué l'état de la résolution du contenu. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Constants/PTPlacementType.html" format="html" scope="external"> PTPlacementType</a> </td> 
   <td colname="2">Classe qui extrait une demande d'informations de placement. Chaque publicité résolue doit être associée à une information d'emplacement. Les informations d’emplacement indiquent où la publicité doit être placée dans la chronologie. Il contient des informations telles que : 
    <ul id="ul_A9105A78F0C24488BCD5E3F2EE62A3EE"> 
     <li id="li_01E968A4330D4B40BA1EB6F4A6000FFD">Position de placement (en ms) </li> 
     <li id="li_A3DC9498BEE14FBA9E7A5D26874F3984">Type de placement (pré-roulement, mi-roulement ou post-roulement) </li> 
     <li id="li_4B9094DD318B4792854A377CC6064232">Durée du bloc de contenu principal sur le point d'être remplacé </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>