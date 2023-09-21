---
description: MediaPlayer fournit une fonction notifyClick() qui distribue des événements liés à la publicité lorsqu’une publicité cliquable est en cours de lecture. Ces événements fournissent des informations sur la coupure publicitaire et la coupure publicitaire que votre application peut utiliser pour offrir la fonctionnalité de clic publicitaire.
title: Gérer les publicités cliquables
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Gérer les publicités cliquables {#handle-clickable-ads}

MediaPlayer fournit une fonction notifyClick() qui distribue des événements liés à la publicité lorsqu’une publicité cliquable est en cours de lecture. Ces événements fournissent des informations sur la coupure publicitaire et la coupure publicitaire que votre application peut utiliser pour offrir la fonctionnalité de clic publicitaire.

MediaPlayer déclenche les événements suivants lorsqu’une publicité cliquable est lue :

* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_CLICKED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

La variable `AdClickedEvent` contient les informations nécessaires au traitement de la fonction de clic publicitaire.

1. Fournissez un contrôle sur votre lecteur afin que les utilisateurs puissent cliquer sur des publicités cliquables.

   Il peut s’agir d’un bouton ou de tout autre élément permettant de capturer le clic de l’utilisateur.
1. Ajoutez un écouteur d’événement pour l’événement de clic publicitaire de l’utilisateur.

   Par exemple :

   ```
   document.getElementById([ 
   <i>your_click_control_id</i>]).addEventListener("click", onAdClick);
   ```

1. Ajoutez un gestionnaire pour l’événement click de l’utilisateur.

   Ce gestionnaire doit inviter MediaPlayer à déclencher la variable `AdClicked` .

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

1. Ajoutez des écouteurs d’événement pour le démarrage de la publicité MediaPlayer, les clics publicitaires et les notifications de fin de publicité.

   ```
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted);
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_CLICKED, onAdClickedEvent);
   ```

1. Ajoutez des gestionnaires d’événements.
a. Gérez l’événement de début de publicité.
Cela peut tout faire, comme configurer l’interface utilisateur de l’utilisateur.

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

   b. Gérez l’événement sur lequel l’utilisateur a cliqué.
Dans cet exemple, nous obtenons des informations sur les publicités de l’événement et nous ouvrons une nouvelle fenêtre de navigateur à l’aide de ces informations :

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

   c. Gérez l’événement de fin de publicité.

   ```
   onAdCompleted = function (event) { 
       if (clickAddButton) { 
           clickAddButton.setAttribute('hidden', 'true'); 
       } 
   }
   ```
