---
description: TVSDK vous fournit des informations pour que vous puissiez agir sur les publicités par clics publicitaires. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider de la manière dont vous répondez lorsqu’un utilisateur clique sur une publicité cliquable.
seo-description: TVSDK vous fournit des informations pour que vous puissiez agir sur les publicités par clics publicitaires. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider de la manière dont vous répondez lorsqu’un utilisateur clique sur une publicité cliquable.
seo-title: Publicités cliquables
title: Publicités cliquables
uuid: edefbc66-2d30-441d-9c30-256588504463
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Publicités cliquables {#clickable-ads}

TVSDK vous fournit des informations pour que vous puissiez agir sur les publicités par clics publicitaires. Lorsque vous créez l’interface utilisateur du lecteur, vous devez décider de la manière dont vous répondez lorsqu’un utilisateur clique sur une publicité cliquable.

Pour TVSDK pour l’exécution Flash, seules les publicités linéaires peuvent être cliquées.

## Répondre aux clics sur les publicités {#respond-to-clicks-on-ads}

Lorsqu’un utilisateur clique sur une publicité ou un bouton associé, votre application est responsable de répondre. TVSDK vous fournit des informations sur l’URL de destination.

Cet exemple illustre une méthode possible de gestion des clics publicitaires.

1. Chaque fois qu’une publicité est lue, affichez un bouton au-dessus du lecteur multimédia. Un utilisateur qui clique sur la publicité est redirigé vers l’URL de la publicité. Ce bouton fait partie du [!DNL ClickableAdsOverlay.xml].

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

1. Insérez cette incrustation dans l’exemple de lecteur multimédia [!DNL psdkdemo.xml].

   ```xml
      <psdk:ClickableAdsOverlay id="clickableAdsOverlay"  
       visible="false"   top="10" right="0" left="0"  
       text="Click here for more information"   
       click="onAdsOverlayClicked()" 
   </psdk:ClickableAdsOverlay
   ```

1. Pour rendre le visible uniquement lorsqu’une publicité est en cours de lecture, écoutez le  `onAdStart` et le  de `onAdComplete` distribués par .

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

1. Surveillez les interactions des utilisateurs sur les annonces cliquables. Lorsque l’utilisateur touche ou clique sur la publicité ou le bouton, avertissez TVSDK avec `notifyClick`.

   ```
   private function onAdsOverlayClicked():void {     
       _mediaPlayer.view.notifyClick(); 
   }
   ```

1. Écoute le `AdclickEvent.AD_CLICK` .

   Si une publicité est en cours de lecture, TVSDK distribue le `AdClickEvent.AD_CLICK` , à partir duquel vous pouvez récupérer l’URL de clic publicitaire et les informations connexes.

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

1. Affichez l’URL de clic publicitaire et toutes les informations connexes.

       Vous pouvez, par exemple, l’afficher de l’une des manières suivantes :
   
   * Ouvrez l’URL de clic publicitaire dans un navigateur de votre application.

      Sur les plates-formes de bureau, la zone de lecture des publicités vidéo est généralement utilisée pour appeler les URL de clic publicitaire lorsque l’utilisateur clique dessus.
   * Redirigez l’utilisateur vers le navigateur Web mobile externe.

      Sur les périphériques mobiles, la zone de lecture des publicités vidéo est utilisée pour d’autres fonctions, telles que le masquage et l’affichage des commandes, la mise en pause de la lecture, le développement en plein écran, etc. Par conséquent, sur les périphériques mobiles, un  distinct, tel qu’un bouton de sponsor, est généralement présenté à l’utilisateur comme moyen de lancer l’URL de clic publicitaire.

1. Fermez la fenêtre du navigateur dans laquelle les informations de clic publicitaire sont affichées et relancez la lecture de la vidéo.
