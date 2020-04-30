---
description: Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser le navigateur TVSDK à écouter les événements liés aux publicités.
seo-description: Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser le navigateur TVSDK à écouter les événements liés aux publicités.
seo-title: Afficher les bannières publicitaires
title: Afficher les bannières publicitaires
uuid: aabc126e-b3aa-42dd-ab50-a7db8e324c50
translation-type: tm+mt
source-git-commit: ''

---


# Afficher les bannières publicitaires {#display-banner-ads}

Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser le navigateur TVSDK à écouter les événements liés aux publicités.

Le navigateur TVSDK fournit une liste de bannières publicitaires associées associées à une publicité linéaire par le biais du `AdobePSDK.PSDKEventType.AD_STARTED` événement.

Les manifestes peuvent spécifier des bannières publicitaires complémentaires en :

* Un extrait de code HTML
* URL d’une page iFrame
* URL d’une image statique ou d’un fichier SWF Adobe Flash

Pour chaque publicité connexe, le navigateur TVSDK indique les types disponibles pour votre application.

Ajouter un écouteur pour le événement `AdobePSDK.PSDKEventType.AD_STARTED` qui effectue les opérations suivantes :
1. Efface les publicités existantes dans l’instance de bannière.
1. Obtient la liste des publicités complémentaires de `Ad.getCompanionAssets`.
1. Si la liste des publicités complémentaires n’est pas vide, effectuez une itération sur la liste pour les instances de bannière.

   Chaque instance de bannière (une `AdBannerAsset`) contient des informations, telles que la largeur, la hauteur, le type de ressource (html, iframe ou static) et les données requises pour afficher la bannière correspondante.
1. Si une publicité vidéo ne comporte aucune publicité connexe, la liste des ressources d’accompagnement ne contient aucune donnée pour cette publicité vidéo.
1. Envoie les informations de la bannière à une fonction de votre page qui affiche les bannières à l’emplacement approprié.

   Il s’agit généralement d’un `div`et votre fonction utilise le `div ID` pour afficher la bannière. Par exemple :

   Ajouter l’écouteur de événement :

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   Mettez en oeuvre le gestionnaire d’écouteurs :

   ```js
   private function onAdStarted(event:AdPlaybackEvent):void 
   { 
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
   function displayCompanion (resourceType, width, height, data) { 
       console.log(resourceType + "," +  width + "," +  height); 
       var bannerDiv = document.getElementById('banner' + width + 'x' + height);  
   
       // Assuming that there is an HTML element on the page  
       // with an id of "banner300x250", for example 
       if (bannerDiv !== null) { 
           bannerDiv.innerHTML = data; 
       } 
   }
   ```

