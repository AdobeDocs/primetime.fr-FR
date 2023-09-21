---
description: Le navigateur TVSDK fournit des outils pour créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime.
title: Basculement Flash
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Basculement Flash {#flash-failover}

Le navigateur TVSDK fournit des outils pour créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime.

Utilisez les outils de votre plateforme pour créer un lecteur et le connecter à la vue du lecteur multimédia dans le navigateur TVSDK, qui dispose de méthodes de lecture et de gestion des vidéos. Par exemple, le navigateur TVSDK fournit des méthodes de lecture et de pause. Vous pouvez créer des boutons d’interface utilisateur sur votre plateforme et définir les boutons pour appeler ces méthodes Browser TVSDK.

## Flash de secours {#section_92D3884A13A6431F9A9CC5C79715D888}

Dans Browser TVSDK, votre application interagit uniquement avec la variable `Primetime.js` API. L’implémentation du Browser TVSDK sous-jacent décide de la technologie du lecteur à utiliser en fonction de la plateforme actuelle et du type de ressource du média à lire.

La décision concernant la technologie du lecteur n’est pas prise tant que vous n’avez pas appelé `MediaPlayer.replaceCurrentResource` pour lire une ressource spécifique.

Par exemple :

```js
var player = new AdobePSDK.MediaPlayer(), 
              mediaResource = new AdobePSDK.MediaResource(url, 
              AdobePSDK.MediaResource.Type.TYPE_HLS); 
              ... 
              player.replaceCurrentResource(mediaResource);
```

## Déterminer le lecteur multimédia à utiliser {#section_D844E386AF5848688D204DEE258ECEE6}

Cet exemple de procédure illustre le processus de détermination de la technologie du lecteur :

>[!TIP]
>
>Le processus peut varier en fonction de l’URL et de votre environnement.

1. Si les extensions source de média sont prises en charge, utilisez-les sans limites connues.
1. Si cette méthode est prise en charge, utilisez la méthode `<video>` balise directement sans MSE.
1. Assurez-vous d’utiliser au moins la version 23.0 d’Adobe Flash Player.
1. Si aucune technologie de lecture appropriée n’est trouvée, `replaceCurrentResource` renvoie une erreur.

Une `replaceCurrentResource` appel sur le même `MediaPlayer` suit le même processus. Vous pouvez ainsi lire différents types de ressources en utilisant la même `MediaPlayer` instance dans le même parent `<DIV>` que vous avez spécifié lorsque la variable `MediaPlayerView` a été créée.

>[!TIP]
>
>Objet SWF et `<video>` sont imbriquées dans la balise parent. `<DIV>` balise .
