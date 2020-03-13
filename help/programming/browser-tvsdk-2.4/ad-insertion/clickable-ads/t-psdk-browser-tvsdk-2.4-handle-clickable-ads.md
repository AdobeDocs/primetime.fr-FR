---
description: MediaPlayer fournit une fonction notificationClick() qui distribue des  liées aux publicités lorsqu’une publicité cliquable est en cours de lecture. Ces  fournissent des informations sur les coupures publicitaires et publicitaires que votre application peut utiliser pour fournir une fonctionnalité de clics publicitaires.
seo-description: MediaPlayer fournit une fonction notificationClick() qui distribue des  liées aux publicités lorsqu’une publicité cliquable est en cours de lecture. Ces  fournissent des informations sur les coupures publicitaires et publicitaires que votre application peut utiliser pour fournir une fonctionnalité de clics publicitaires.
seo-title: Gestion des publicités cliquables
title: Gestion des publicités cliquables
uuid: 5d3c9d36-60d7-4272-a523-7d1fe0e1615f
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Gestion des publicités cliquables {#handle-clickable-ads}

MediaPlayer fournit une fonction notificationClick() qui distribue des  liées aux publicités lorsqu’une publicité cliquable est en cours de lecture. Ces  fournissent des informations sur les coupures publicitaires et publicitaires que votre application peut utiliser pour fournir une fonctionnalité de clics publicitaires.

Le lecteur multimédia déclenche le  suivant lorsqu’une publicité cliquable est lue :

* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_CLICKED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

Le `AdClickedEvent` contient les informations nécessaires au traitement de la fonction de clic publicitaire.

1. Fournissez un contrôle dans votre lecteur pour que les utilisateurs puissent cliquer sur des publicités cliquables.

   Il peut s’agir d’un bouton ou de tout autre élément permettant de capturer le clic de l’utilisateur.
1. Ajouter un  d’écouteur pour l’ensemble des clics publicitaires de l’utilisateur .

   Par exemple :

   ```
   document.getElementById([ 
   <i>your_click_control_id</i>]).addEventListener("click", onAdClick);
   ```

1. Ajouter un gestionnaire pour le de clics de l’utilisateur .

   Ce gestionnaire doit demander au lecteur multimédia de déclencher le `AdClicked` .

   ```
   onAdClick = function (event) { 
       // Get a reference to your player 
       var player = getPlayer(); 
       if (player) { 
           // Call the MediaPlayer's notifyClick function 
           // which gets MediaPlayer to fire AdClicked 
           player.notifyClick(); 
       } 
   } 
   ```

1. Ajouter des  d’écoute pour le lecteur multimédia, l’utilisateur a cliqué sur la publicité et a terminé les notifications.

   ```
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted);
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_CLICKED, onAdClickedEvent);
   ```

1. Ajouter gestionnaires de  de.
a. Gérez le  de publicité le .
Cela peut être utile, comme la configuration de l’interface utilisateur pour l’utilisateur.

   ```
   onAdStarted = function (event) { 
       if (clickAddButton && event && event.ad) { 
           var adClick = event.ad.primaryAsset && event.ad.primaryAsset.adClick; 
           if (adClick && adClick.isValid) { 
               // Do some initial processing  
               // when the ad starts, prior 
               // to the user's click. 
           } 
       } 
   }
   ```

   b. Gérez le sur lequel l’utilisateur a cliqué.
Dans cet exemple, nous obtenons des informations sur les publicités du  et ouvrons une nouvelle fenêtre du navigateur à l’aide de ces informations :

   ```
   onAdClickedEvent = function (event) { 
       if (event && event.ad) { 
           var adClick = event.adClick; 
           if (!(adClick && adClick.isValid)) { 
               adClick = event.ad.primaryAsset && event.ad.primaryAsset.adClick; 
           } 
           if (adClick && adClick.isValid) 
           { 
               // Do something with the currently playing ad 
               window.open(adClick.url); 
           } 
       } 
   }
   ```

   c. Gérez le  de la publicité terminée.

   ```
   onAdCompleted = function (event) { 
       if (clickAddButton) { 
           clickAddButton.setAttribute('hidden', 'true'); 
       } 
   }
   ```
