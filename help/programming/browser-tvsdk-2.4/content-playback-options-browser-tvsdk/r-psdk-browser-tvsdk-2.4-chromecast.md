---
description: Vous pouvez diffuser n’importe quelle diffusion depuis une application d’expéditeur basée sur TVSDK et faire en sorte que la diffusion soit lue sur Chromecast avec Browser TVSDK.
title: Application Google Cast pour Browser TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Application Google Cast pour Browser TVSDK{#google-cast-app-for-browser-tvsdk}

Vous pouvez diffuser n’importe quelle diffusion depuis une application d’expéditeur basée sur TVSDK et faire en sorte que la diffusion soit lue sur Chromecast avec Browser TVSDK.

<!--<a id="section_87CE5D6D46F0439EB6E63A742D6DD9C8"></a>-->

Il existe deux composants d’une application avec fonction de diffusion :

* L’application d’expéditeur, qui agit comme la télécommande.

  Les applications d’expéditeur comprennent les smartphones, les ordinateurs personnels, etc. L’application peut être développée à l’aide de SDK natifs pour iOS, Android et Chrome.
* L’application récepteur, qui s’exécute sur Chromecast et lit le contenu.

  >[!IMPORTANT]
  >
  >Cette application ne peut être qu’une application HTML5.

L’expéditeur et le destinataire communiquent en utilisant les SDK de diffusion pour transmettre les messages.

## Processus de base {#section_FAF680FF29DA4D24A50AC0A2B6402B58}

Voici un aperçu du processus :

1. L’application expéditeur établit une connexion avec l’application récepteur.
1. L’application d’expéditeur envoie un message pour charger le média sur l’application du récepteur.
1. L’application du récepteur commence la lecture.
1. L’application d’expéditeur envoie à l’application récepteur des messages de contrôle de lecture, tels que play, pause, search, fast forward, fast rewind, rewind, volume change, etc.
1. L’application du récepteur réagit à ces messages.

## Format du message {#section_1624159DD51D4C87B3E5803DEEBCB6B7}

Vous devez définir les messages pour que l&#39;expéditeur et le destinataire puissent comprendre. Voici un exemple de message de recherche :

```js
{ 
"type": "seek", 
"seekTo": 10000 
} 
```

Lors de l’envoi de messages personnalisés tels que le message de recherche par le biais des SDK de diffusion, un espace de noms de message personnalisé est requis. Voici un exemple en JavaScript :

```js
Custom Message Namespace 
var MSG_NAMESPACE = "urn:x-cast:com.adobe.primetime"; 
```

## Établissement d’une connexion {#section_B4D40CABDD3E46FDBE7B5651DFF91653}

>[!IMPORTANT]
>
>Les API TVSDK du navigateur ne sont pas impliquées lors de la configuration de la connexion.

Pour établir une connexion, l&#39;expéditeur et le destinataire doivent effectuer les tâches suivantes :

* L’expéditeur doit consulter la documentation de la plateforme à l’adresse [Développement d’applications d’expéditeur](https://developers.google.com/cast/docs/sender_apps).
* Le récepteur utilise les API du récepteur de diffusion pour établir une connexion avec l’application de l’expéditeur. Par exemple :

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

Pour envoyer des messages au destinataire, consultez la documentation de la plateforme de votre expéditeur.

>[!IMPORTANT]
>
>Vous devez inclure l’espace de noms du message personnalisé, `MSG_NAMESPACE` dans tous les messages.

Pour l’application récepteur, suivez la documentation relative aux API du récepteur de diffusion.

**Exemple de message d’expéditeur basé sur Chrome**

```js
window.session.sendMessage(MSG_NAMESPACE, message, successCallback, errorCallback); //https://developers.google.com/cast/docs/reference/chrome/chrome.cast.Session#sendMessage
```

**Gestion des événements d’expéditeur basés sur Chrome**

Liez les gestionnaires d’événements à vos éléments d’interface utilisateur qui envoient des messages lorsque les événements correspondants sont déclenchés. Par exemple, pour une application d’expéditeur Chrome, l’événement de recherche peut être envoyé comme suit :

```js
document.getElementById("#seekBar").addEventListener("click", seekEventHandler); 
   
function seekEventHandler(event) { 
    seekMessage = { type: "seek", seekTo: player.currentTime }; //player is an instance of AdobePSDK.MediaPlayer 
    window.session.sendMessage(MSG_NAMESPACE, seekMessage, successCallback, errorCallback); 
} 
```

**Gestion des messages du destinataire**

Voici un exemple de gestion du message de recherche à partir de l’application du récepteur :

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
