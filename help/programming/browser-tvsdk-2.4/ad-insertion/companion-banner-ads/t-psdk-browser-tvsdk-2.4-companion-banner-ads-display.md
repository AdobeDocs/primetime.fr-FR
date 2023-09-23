---
description: Pour afficher les bannières publicitaires, vous devez créer des instances de bannière et permettre au TVSDK du navigateur d’écouter les événements liés aux publicités.
title: Afficher les bannières publicitaires
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Afficher les bannières publicitaires {#display-banner-ads}

Pour afficher les bannières publicitaires, vous devez créer des instances de bannière et permettre au TVSDK du navigateur d’écouter les événements liés aux publicités.

TVSDK du navigateur fournit une liste des bannières publicitaires compagnons associées à une publicité linéaire par le biais de la variable `AdobePSDK.PSDKEventType.AD_STARTED` .

Les manifestes peuvent spécifier des bannières publicitaires d’accompagnement en :

* Fragment de HTML
* URL d’une page iFrame
* URL d’une image statique ou d’un fichier de SWF de Flash Adobe

Pour chaque publicité compagnon, le Browser TVSDK indique les types disponibles pour votre application.

Ajouter un écouteur pour l’événement `AdobePSDK.PSDKEventType.AD_STARTED` qui effectue les opérations suivantes :
1. Efface les publicités existantes dans l’instance de bannière.
1. Récupère la liste des publicités compagnons à partir de `Ad.getCompanionAssets`.
1. Si la liste des publicités d’accompagnement n’est pas vide, passez la souris sur la liste pour les instances de bannière.

   Chaque instance de bannière (une `AdBannerAsset`) contient des informations, telles que la largeur, la hauteur, le type de ressource (html, iframe ou statique), ainsi que les données requises pour afficher la bannière compagnon.
1. Si une publicité vidéo ne comporte aucune publicité compagnon enregistrée, la liste des ressources compagnons ne contient aucune donnée pour cette publicité vidéo.
1. Envoie les informations sur la bannière à une fonction de votre page qui affiche les bannières à un emplacement approprié.

   Il s’agit généralement d’une `div`, et votre fonction utilise la fonction `div ID` pour afficher la bannière. Par exemple :

   Ajoutez l’écouteur d’événement :

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   Implémentez le gestionnaire d’écouteurs :

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

   Exemple de JavaScript pour gérer l&#39;affichage :

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
