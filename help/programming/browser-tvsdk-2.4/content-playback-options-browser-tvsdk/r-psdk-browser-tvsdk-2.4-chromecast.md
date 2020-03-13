---
description: Vous pouvez diffuser n’importe quel flux depuis une application d’expéditeur basée sur TVSDK et faire lire le flux sur Chromecast avec le navigateur TVSDK.
seo-description: Vous pouvez diffuser n’importe quel flux depuis une application d’expéditeur basée sur TVSDK et faire lire le flux sur Chromecast avec le navigateur TVSDK.
seo-title: Application Google Cast pour navigateur TVSDK
title: Application Google Cast pour navigateur TVSDK
uuid: 018143e2-143a-4f88-97c6-4b10a2083f9e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Application Google Cast pour navigateur TVSDK{#google-cast-app-for-browser-tvsdk}

Vous pouvez diffuser n’importe quel flux depuis une application d’expéditeur basée sur TVSDK et faire lire le flux sur Chromecast avec le navigateur TVSDK.

<!--<a id="section_87CE5D6D46F0439EB6E63A742D6DD9C8"></a>-->

Il existe deux composants d’une application compatible avec le mode diffusion :

* L&#39;application d&#39;expéditeur, qui agit comme la télécommande.

   Les applications d’expéditeur comprennent les smartphones, les ordinateurs personnels, etc. L’application peut être développée à l’aide de kits SDK natifs pour iOS, Android et Chrome.
* L’application destinataire, qui s’exécute sur Chromecast et lit le contenu.

   >[!IMPORTANT]
   >
   >Cette application ne peut être qu’une application HTML5.

L’expéditeur et le destinataire communiquent en utilisant les SDK de diffusion pour transmettre des messages.

## Processus de base {#section_FAF680FF29DA4D24A50AC0A2B6402B58}

Voici un aperçu du processus :

1. L’application d’expéditeur établit une connexion avec l’application destinataire.
1. L’application d’expéditeur envoie un message pour charger le média sur l’application destinataire.
1. L’application du destinataire commence la lecture.
1. L’application d’expéditeur envoie des messages de contrôle de la lecture, tels que play, pause, recherche, avance rapide, rembobinage rapide, rembobinage, modification du volume, etc., à l’application destinataire.
1. L’application du destinataire réagit à ces messages.

## Format du message {#section_1624159DD51D4C87B3E5803DEEBCB6B7}

Vous devez définir les messages pour que l&#39;expéditeur et le destinataire puissent comprendre. Voici un exemple de message de recherche :

```js
{ 
"type": "seek", 
"seekTo": 10000 
} 
```

Lors de l’envoi de messages personnalisés, tels que le message de recherche via les kits SDK de diffusion, un message personnalisé   est requis. Voici un exemple dans JavaScript :

```js
Custom Message Namespace 
var MSG_NAMESPACE = "urn:x-cast:com.adobe.primetime"; 
```

## Etablissement d’une connexion {#section_B4D40CABDD3E46FDBE7B5651DFF91653}

>[!IMPORTANT]
>
>Les API du navigateur TVSDK ne sont pas impliquées lors de l’établissement de la connexion.

Pour établir une connexion, l’expéditeur et le destinataire doivent compléter le  suivant :

* L’expéditeur doit consulter la documentation relative à la plate-forme dans [Sender App Development](https://developers.google.com/cast/docs/sender_apps).
* Le destinataire utilise les API du récepteur Cast pour établir une connexion avec l’application de l’expéditeur. Par exemple :

   ```js
   window.castReceiverManager = cast.receiver.CastReceiverManager.getInstance(); 
   
   window.castReceiverManager.onReady = function (event) { /*handle event*/ }; 
   window.castReceiverManager.onSenderConnected = function (event) { /*handle event*/ }; 
   window.castReceiverManager.onSenderDisconnected = function (event) { /*handle event*/ }; 
   
   var customMessageBus = window.castReceiverManager.getCastMessageBus(MSG_NAMESPACE); 
   customMessageBus.onMessage = function (event) { /*handle messages*/ }; 
   
   window.castReceiverManager.start(); 
   ```

## Gestion des messages {#section_3E4814546F5946C9B3E7A1AE384B4FF8}

Pour envoyer des messages au destinataire, reportez-vous à la documentation de la plate-forme de votre expéditeur.

>[!IMPORTANT]
>
>Vous devez inclure le message personnalisé   de `MSG_NAMESPACE` dans tous les messages.

Pour l’application de réception, suivez la documentation relative aux API de réception de distribution.

**Exemple d’un message d’expéditeur basé sur Chrome**

```js
window.session.sendMessage(MSG_NAMESPACE, message, successCallback, errorCallback); //https://developers.google.com/cast/docs/reference/chrome/chrome.cast.Session#sendMessage
```

**Gestion des de l’expéditeur basé sur Chrome**

Liez les gestionnaires de  à vos éléments d’interface utilisateur qui enverront des messages lorsque le correspondant  est déclenché. Par exemple, pour une application d’expéditeur basée sur Chrome, le de recherche peut être envoyé comme suit :

```js
document.getElementById("#seekBar").addEventListener("click", seekEventHandler); 
   
function seekEventHandler(event) { 
    seekMessage = { type: "seek", seekTo: player.currentTime }; //player is an instance of AdobePSDK.MediaPlayer 
    window.session.sendMessage(MSG_NAMESPACE, seekMessage, successCallback, errorCallback); 
} 
```

**Gestion des messages du destinataire**

Voici un exemple de gestion du message de recherche à partir de l’application du destinataire :

```js
customMessageBus.onMessage = function (event) { 
    var message = JSON.parse(event.data); 
    switch (message.type) { 
        case "seek":  
            player.seek(parseInt(message.seekTo)); 
            break; 
        //code for handling other events 
        default:  
            break; 
    } 
}; 
```

