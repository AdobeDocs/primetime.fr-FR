---
description: TVSDK prend en charge les bannières publicitaires connexes, qui accompagnent une publicité linéaire et restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l’affichage des bannières compagnons fournies avec une publicité linéaire.
title: Bannières publicitaires d’accompagnement
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# Bannières publicitaires d’accompagnement {#companion-banner-ads}

TVSDK prend en charge les bannières publicitaires connexes, qui accompagnent une publicité linéaire et restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l’affichage des bannières compagnons fournies avec une publicité linéaire.

Lors de l’affichage des publicités compagnons, procédez comme suit :

* Essayez de présenter autant de bannières publicitaires d’accompagnement que vous le souhaitez dans la disposition de votre lecteur.
* Présenter une bannière compagnon uniquement si vous disposez d’un emplacement correspondant exactement à sa hauteur et largeur spécifiées.

  >[!TIP]
  >
  >Ne redimensionnez pas la bannière.

* Présenter la ou les bannières d’accompagnement dès que possible après le début de la publicité.
* Ne superposez pas le conteneur publicitaire/vidéo principal avec les bannières compagnons.
* Continuez à afficher les bannières compagnons une fois la publicité terminée.

  La norme consiste à afficher chaque bannière compagnon jusqu’à ce que vous ayez un remplacement pour cette bannière.

## Companion banner data {#companion-banner-data}

Le contenu d’une AdBannerAsset décrit une bannière compagnon.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

La variable `AdPlaybackEvent.AD_STARTED` renvoie un événement `Ad` qui contient une instance `companionAssets` property ( `Vector.<AdAsset>`).
Chaque `AdAsset` fournit des informations sur l’affichage de la ressource.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Informations disponibles </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> Largeur de la bannière compagnon en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> Hauteur de la bannière compagnon en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> type de ressource </td> 
   <td colname="col2">Type de ressource pour cette bannière compagnon : 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html : les données se trouvent dans le code du HTML. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe : les données sont une URL iframe (src). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> données de bannière </td> 
   <td colname="col2"> Les données du type spécifié par <span class="codeph"> resourceType</span> pour cette bannière compagnon. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> URL statique </td> 
   <td colname="col2"> <p>Parfois, la bannière compagnon comporte également une valeur staticURL qui est une URL directe vers l’image ou vers une <span class="filepath"> .swf</span> (bannière Flash). </p> <p>Si vous ne souhaitez pas utiliser de code html ou iframe, vous pouvez utiliser une URL directe vers une image ou un fichier swf pour afficher la bannière dans l’étape du Flash. Dans ce cas, vous pouvez utiliser staticURL pour afficher la bannière. </p> <p>Important : Vous devez vérifier si l’URL statique est une chaîne valide, car cette propriété peut ne pas toujours être disponible. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Afficher les bannières publicitaires {#display-banner-ads}

Pour afficher les bannières publicitaires, vous devez créer des instances de bannière et permettre à TVSDK d’écouter les événements liés aux publicités.

TVSDK fournit une liste des bannières publicitaires associées à une publicité linéaire par le biais de la variable `AdPlaybackEvent.AD_STARTED` événement .

Les manifestes peuvent spécifier des bannières publicitaires d’accompagnement en :

* Fragment de HTML
* URL d’une page iFrame
* URL d’une image statique ou d’un fichier de SWF de Flash Adobe

Pour chaque publicité compagnon, TVSDK indique les types disponibles pour votre application.

Ajoutez un écouteur pour la fonction `AdPlaybackEvent.AD_STARTED` qui effectue les opérations suivantes :

1. Efface les publicités existantes dans l’instance de bannière.

1. Récupère la liste des publicités compagnons à partir de `Ad.companionAssets`.

1. Si la liste des publicités d’accompagnement n’est pas vide, passez la souris sur la liste pour les instances de bannière.

   Chaque instance de bannière ( `AdBannerAsset`) contient des informations, telles que la largeur, la hauteur, le type de ressource (html, iframe ou statique), ainsi que les données requises pour afficher la bannière compagnon.

1. Si une publicité vidéo ne comporte aucune publicité compagnon enregistrée, la liste des ressources compagnons ne contient aucune donnée pour cette publicité vidéo.

   Pour afficher une publicité d’affichage autonome, ajoutez la logique à votre script afin d’exécuter une balise d’affichage publicitaire standard DFP (DoubleClick for Publishers) dans l’instance de bannière appropriée.

1. Envoie les informations de la bannière à une fonction de votre page, généralement à l’aide de JavaScript, en utilisant `ExternalInterface`, qui affiche les bannières à un emplacement approprié.

   Il s’agit généralement d’une `div`, et votre fonction utilise la fonction `div ID` pour afficher la bannière. Par exemple :

   Ajoutez l’écouteur d’événement :

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   Implémentez le gestionnaire d’écouteurs :

   ```js
   private function onAdStarted(event:AdPlaybackEvent):void { 
       // check if there are any companion banner 
       if (event.ad && event.ad.companionAssets  
                    && event.ad.companionAssets.length > 0) { 
           for each (var banner:AdBannerAsset in event.ad.companionAssets) { 
               if (ExternalInterface.available) { 
                   //-- call the java script that will handle the banner display. 
                   ExternalInterface.call('addBanner', banner.resourceType,  
                       banner.width, banner.height, banner.bannerData); 
               } 
           } 
       }  
       //...        
   }
   ```

   Exemple de JavaScript pour gérer l&#39;affichage :

   ```js
   function addBanner(resourceType, width, height, data) { 
       console.log(resourceType + "," +  width + "," +  height); 
   
   //Assume an html element on the page with id like 'banner300x250' 
       var bannerDiv = document.getElementById('banner' + width +  
           'x' + height);  
       if (bannerDiv != null) { 
           if (resourceType == "html") { // for html resource 
               bannerDiv.innerHTML = data; 
           } 
           else if (resourceType == "iframe") { // for iframe resource 
               bannerDiv.innerHTML = "<iframe src='" + data +  
                   "' width='100%' height='100%'></iframe>"; 
           } 
       } 
   }
   ```
