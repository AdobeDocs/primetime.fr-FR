---
description: TVSDK fournit des informations qui vous permettent d’agir sur les publicités par clic publicitaire. Lorsque vous créez l’interface utilisateur de votre lecteur, vous devez décider comment répondre lorsqu’un utilisateur clique sur une publicité cliquable.
title: Publicités cliquables
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Publicités cliquables {#clickable-ads}

TVSDK fournit des informations qui vous permettent d’agir sur les publicités par clic publicitaire. Lorsque vous créez l’interface utilisateur de votre lecteur, vous devez décider comment répondre lorsqu’un utilisateur clique sur une publicité cliquable.

Pour TVSDK pour Flash Runtime, seules les publicités linéaires peuvent être cliquées.

## Réponse aux clics sur les publicités {#respond-to-clicks-on-ads}

Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, votre application est responsable de répondre. TVSDK vous fournit des informations sur l’URL de destination.

Cet exemple présente un moyen possible de gérer les clics publicitaires.

1. Chaque fois qu’une publicité est lue, un bouton s’affiche au-dessus du lecteur multimédia. Un utilisateur qui clique sur la publicité est redirigé vers l’URL de la publicité. Ce bouton fait partie de la [!DNL ClickableAdsOverlay.xml].

   ```xml
      <?xml version="1.0"?> 
   <s:VGroup xmlns:fx="https://ns.adobe.com/mxml/2009"  
       xmlns:s="library://ns.adobe.com/flex/spark" percentWidth="100" horizontalAlign="center">     
           <fx:Declarations><fx:String id="text"/></fx:Declarations> 
           <s:Label text="{text}"  backgroundAlpha="0.75" backgroundColor="#DEDEDE"  
               color="#000000" paddingBottom="5" paddingRight="5" paddingLeft="5"  
               paddingTop="5"/> 
   </s:VGroup>
   ```

1. Inclure cette superposition sur l’exemple de lecteur multimédia, [!DNL psdkdemo.xml].

   ```xml
      <psdk:ClickableAdsOverlay id="clickableAdsOverlay"  
       visible="false"   top="10" right="0" left="0"  
       text="Click here for more information"   
       click="onAdsOverlayClicked()" 
   </psdk:ClickableAdsOverlay
   ```

1. Pour que la vue ne soit visible que lors de la lecture d’une publicité, écoutez la fonction `onAdStart` et `onAdComplete` événements distribués par .

   ```
   _player.addEventListener(AdPlaybackEvent.AD_STARTED, onAdStarted); 
   _player.addEventListener(AdPlaybackEvent.AD_COMPLETED, onAdCompleted); 
   ```

   ```
      private function onAdStarted(event:AdPlaybackEvent):void { 
       var primaryAsset:AdAsset = event.ad.primaryAsset; 
       if (primaryAsset.adClick != null) { 
           clickableAdsOverlay.visible = true;  
       } 
   } 
   private function onAdCompleted(event:AdPlaybackEvent):void { 
       clickableAdsOverlay.visible = false; 
   }
   ```

1. Surveillez les interactions des utilisateurs sur les annonces cliquables. Lorsque l’utilisateur touche ou clique sur la publicité ou le bouton, informez TVSDK de `notifyClick`.

   ```
   private function onAdsOverlayClicked():void {     
       _mediaPlayer.view.notifyClick(); 
   }
   ```

1. Écoute de la `AdclickEvent.AD_CLICK` .

   Si une publicité est en cours de lecture, TVSDK distribue la variable `AdClickEvent.AD_CLICK` , à partir de laquelle vous pouvez récupérer l’URL du clic publicitaire et les informations associées.

   ```
      _player.addEventListener(AdClickEvent.AD_CLICK, onAdClick);
   ```

1. Mettez le lecteur multimédia en pause lors de la redirection de l’utilisateur vers l’URL de la publicité.

   ```
   private function onAdClick(event:AdClickEvent):void { 
       _logger.info("#onAdClick Ad clicked. Target url is {0}", event.adClick.url);  
       _player.pause(); 
       var adRequest:URLRequest = new URLRequest(event.adClick.url); 
       navigateToURL(adRequest, event.adClick.title); 
   }
   ```

1. Affichez l’URL de clic publicitaire et toutes les informations associées.

       Par exemple, vous pouvez l’afficher de l’une des manières suivantes :
   
   * Ouvrez l’URL du clic publicitaire dans un navigateur de votre application.

     Sur les plateformes de bureau, la zone de lecture des publicités vidéo est généralement utilisée pour appeler les URL de clic publicitaire lorsque l’utilisateur clique.
   * Redirigez l’utilisateur vers le navigateur Web mobile externe.

     Sur les appareils mobiles, la zone de lecture des publicités vidéo est utilisée pour d’autres fonctions, telles que le masquage et l’affichage des commandes, la mise en pause de la lecture, le passage en plein écran, etc. Par conséquent, sur les appareils mobiles, une vue distincte, telle qu’un bouton de parrainage, est généralement présentée à l’utilisateur comme un moyen de lancer l’URL de clic publicitaire.

1. Fermez la fenêtre du navigateur dans laquelle les informations de clic publicitaire s’affichent et relancez la lecture de la vidéo.
