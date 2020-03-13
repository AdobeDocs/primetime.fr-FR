---
description: TVSDK prend en charge les bannières publicitaires associées, qui sont des publicités qui accompagnent une publicité linéaire et qui restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l'affichage des bannières d'accompagnement fournies avec une publicité linéaire.
seo-description: TVSDK prend en charge les bannières publicitaires associées, qui sont des publicités qui accompagnent une publicité linéaire et qui restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l'affichage des bannières d'accompagnement fournies avec une publicité linéaire.
seo-title: Bannières publicitaires d’accompagnement
title: Bannières publicitaires d’accompagnement
uuid: 388a1683-342c-4f3b-97c8-cfcb6c5cfee1
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Bannières publicitaires d’accompagnement {#companion-banner-ads}

TVSDK prend en charge les bannières publicitaires associées, qui sont des publicités qui accompagnent une publicité linéaire et qui restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l&#39;affichage des bannières d&#39;accompagnement fournies avec une publicité linéaire.

Lors de l’affichage des publicités d’accompagnement, suivez les recommandations suivantes :

* Tentez de présenter autant de bannières publicitaires d’accompagnement d’une publicité vidéo que vous le souhaitez dans la mise en page de votre lecteur.
* Présentez une bannière connexe uniquement si vous disposez d’un emplacement qui correspond exactement à sa hauteur et sa largeur spécifiées.

   >[!TIP]
   >
   >Ne redimensionnez pas la bannière.

* Présentez les bannières d’accompagnement dès que possible après le début de la publicité.
* Ne superposez pas le  publicitaire/vidéo principal avec les bannières d’accompagnement.
* Continuez à afficher les bannières d’accompagnement une fois la publicité terminée.

   La norme consiste à afficher chaque bannière d’accompagnement jusqu’à ce que vous ayez un remplaçant pour cette bannière.

## Données de bannière d’accompagnement {#companion-banner-data}

Le contenu d’un AdBannerAsset décrit une bannière connexe.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Le `AdPlaybackEvent.AD_STARTED` renvoie une `Ad` instance contenant une `companionAssets` propriété ( `Vector.<AdAsset>`).
Chacun `AdAsset` fournit des informations sur l’affichage de la ressource.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Informations disponibles </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> largeur </td> 
   <td colname="col2"> Largeur de la bannière d’accompagnement en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> hauteur </td> 
   <td colname="col2"> Hauteur de la bannière d’accompagnement en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> type de ressource </td> 
   <td colname="col2">Type de ressource pour cette bannière connexe : 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html : Les données sont en code HTML. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe : Les données sont une URL iframe (src). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> données de bannière </td> 
   <td colname="col2"> Données du type spécifié par <span class="codeph"> resourceType</span> pour cette bannière connexe. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> URL statique </td> 
   <td colname="col2"> <p>Parfois, la bannière associée comporte également une URL statique qui est une URL directe vers l’image ou vers une <span class="filepath"> .swf</span> (bannière Flash). </p> <p>Si vous ne souhaitez pas utiliser de code html ou iframe, vous pouvez utiliser une URL directe vers une image ou un fichier swf pour afficher la bannière sur l’étape Flash. Dans ce cas, vous pouvez utiliser staticURL pour afficher la bannière. </p> <p>Important :  Vous devez vérifier si l’URL statique est une chaîne valide, car cette propriété peut ne pas toujours être disponible. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Afficher les bannières publicitaires {#display-banner-ads}

Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser TVSDK à écouter les  liées aux publicités.

TVSDK fournit un de bannières publicitaires associées associées à une publicité linéaire par le biais de l’ de  de. `AdPlaybackEvent.AD_STARTED`

Les manifestes peuvent spécifier des bannières publicitaires d&#39;accompagnement par :

* Un extrait de code HTML
* URL d’une page iFrame
* URL d’une image statique ou d’un fichier SWF Adobe Flash

Pour chaque publicité connexe, TVSDK indique les types disponibles pour votre application.

Ajouter un écouteur pour le `AdPlaybackEvent.AD_STARTED` qui effectue les actions suivantes :

1. Efface les publicités existantes dans l’instance de bannière.

1. Obtient le  des publicités d&#39;accompagnement `Ad.companionAssets`.

1. Si le  des publicités complémentaires n’est pas vide, effectuez une itération sur le pour les instances de bannière.

   Chaque instance de bannière (une `AdBannerAsset`) contient des informations, telles que la largeur, la hauteur, le type de ressource (html, iframe ou statique), ainsi que les données requises pour afficher la bannière correspondante.

1. Si une publicité vidéo ne comporte aucune publicité connexe, le  des ressources connexes ne contient aucune donnée pour cette publicité vidéo.

   Pour afficher une publicité d’affichage autonome, ajoutez la logique à votre script afin d’exécuter une balise d’affichage publicitaire d’affichage DFP normale (DoubleClick for Publishers) dans l’instance de bannière appropriée.

1. Envoie les informations de la bannière à une fonction sur votre page, en général du code JavaScript `ExternalInterface`, qui affiche les bannières à un emplacement approprié.

   Il s’agit généralement d’une `div`, et votre fonction utilise la `div ID` pour afficher la bannière. Par exemple :

   Ajouter l’écouteur de  :

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

   Exemple de code JavaScript pour gérer l’affichage :

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
