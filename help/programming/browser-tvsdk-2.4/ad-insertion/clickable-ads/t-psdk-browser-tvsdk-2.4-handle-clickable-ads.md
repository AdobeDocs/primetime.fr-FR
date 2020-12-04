---
description: MediaPlayer fournit une fonction notificationClick() qui distribue des événements liés à la publicité lorsqu’une publicité cliquable est en cours de lecture. Ces événements fournissent des informations sur les coupures publicitaires et publicitaires que votre application peut utiliser pour fournir des fonctionnalités de clics publicitaires.
seo-description: MediaPlayer fournit une fonction notificationClick() qui distribue des événements liés à la publicité lorsqu’une publicité cliquable est en cours de lecture. Ces événements fournissent des informations sur les coupures publicitaires et publicitaires que votre application peut utiliser pour fournir des fonctionnalités de clics publicitaires.
seo-title: Gérer les publicités cliquables
title: Gérer les publicités cliquables
uuid: 5d3c9d36-60d7-4272-a523-7d1fe0e1615f
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Gérer les publicités cliquables {#handle-clickable-ads}

MediaPlayer fournit une fonction notificationClick() qui distribue des événements liés à la publicité lorsqu’une publicité cliquable est en cours de lecture. Ces événements fournissent des informations sur les coupures publicitaires et publicitaires que votre application peut utiliser pour fournir des fonctionnalités de clics publicitaires.

MediaPlayer déclenche les événements suivants lorsqu’une publicité cliquable est lue :

* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_CLICKED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

`AdClickedEvent` contient les informations nécessaires au traitement de la fonction de clic publicitaire.

1. Fournissez un contrôle sur votre lecteur pour permettre aux utilisateurs de cliquer sur des publicités cliquables.

   Il peut s’agir d’un bouton ou de tout autre élément permettant de capturer le clic de l’utilisateur.
1. Ajoutez un écouteur de événement pour le événement de clics publicitaires de l’utilisateur.

   Par exemple :

   ```
   document.getElementById([ 
   <i>your_click_control_id</i>]).addEventListener("click", onAdClick);
   ```

1. Ajoutez un gestionnaire pour le événement de clics de l’utilisateur.

   Ce gestionnaire doit demander au MediaPlayer de déclencher le événement `AdClicked`.

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

1. Ajoutez des écouteurs de événement pour le début publicitaire MediaPlayer, puis cliquez sur la publicité et effectuez des notifications.

   ```
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted);
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_CLICKED, onAdClickedEvent);
   ```

1. Ajouter des gestionnaires de événement.
a. Gérez le événement du début publicitaire.
Cela peut tout faire, comme la configuration de l’interface utilisateur pour l’utilisateur.

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

   b. Gérez le événement de clic de la publicité.
Dans cet exemple, nous obtenons des informations publicitaires du événement et ouvrons une nouvelle fenêtre de navigateur à l’aide de ces informations :

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

   c. Gérez le événement de la publicité terminée.

   ```
   onAdCompleted = function (event) { 
       if (clickAddButton) { 
           clickAddButton.setAttribute('hidden', 'true'); 
       } 
   }
   ```
