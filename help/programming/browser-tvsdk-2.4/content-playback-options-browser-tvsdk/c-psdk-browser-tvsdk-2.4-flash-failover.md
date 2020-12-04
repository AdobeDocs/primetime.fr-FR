---
description: Le navigateur TVSDK fournit des outils permettant de créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime.
seo-description: Le navigateur TVSDK fournit des outils permettant de créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime.
seo-title: 'null'
title: 'null'
uuid: 57b35a5f-87f8-41a2-ad85-300b999dc30b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# Basculement de Flash {#flash-failover}

Le navigateur TVSDK fournit des outils permettant de créer une application de lecteur vidéo avancée (votre lecteur Primetime), que vous pouvez intégrer à d’autres composants Primetime.

Utilisez les outils de votre plate-forme pour créer un lecteur et le connecter à la vue du lecteur multimédia dans le navigateur TVSDK, qui offre des méthodes de lecture et de gestion des vidéos. Par exemple, le navigateur TVSDK fournit des méthodes de lecture et de pause. Vous pouvez créer des boutons d’interface utilisateur sur votre plate-forme et définir les boutons pour appeler ces méthodes de navigateur TVSDK.

## Flash de secours {#section_92D3884A13A6431F9A9CC5C79715D888}

Dans le navigateur TVSDK, votre application interagit uniquement avec l’API `Primetime.js`. L’implémentation sous-jacente du navigateur TVSDK détermine la technologie du lecteur à utiliser en fonction de la plate-forme actuelle et du type de ressource du média à lire.

La décision concernant la technologie du lecteur n&#39;est prise que lorsque vous appelez `MediaPlayer.replaceCurrentResource` pour jouer une ressource spécifique.

Par exemple :

```js
var player = new AdobePSDK.MediaPlayer(), 
              mediaResource = new AdobePSDK.MediaResource(url, 
              AdobePSDK.MediaResource.Type.TYPE_HLS); 
              ... 
              player.replaceCurrentResource(mediaResource);
```

## Déterminer le lecteur de médias à utiliser {#section_D844E386AF5848688D204DEE258ECEE6}

Cet exemple de procédure illustre le processus de détermination de la technologie du lecteur :

>[!TIP]
>
>Le processus peut varier en fonction de l’URL et de votre environnement.

1. Si les extensions Media Source sont prises en charge, utilisez-les sans limites connues.
1. Si elle est prise en charge, utilisez la balise `<video>` directement sans MSE.
1. Assurez-vous d’utiliser au moins Adobe Flash Player version 23.0.
1. Si aucune technologie de lecture adaptée n’est trouvée, `replaceCurrentResource` renvoie une erreur.

Un appel suivant `replaceCurrentResource` sur la même instance `MediaPlayer` suit le même processus. Cela vous permet de lire divers types de ressources en utilisant la même instance `MediaPlayer` dans la même balise parente `<DIV>` que celle que vous avez spécifiée lors de la création de l&#39;instance `MediaPlayerView`.

>[!TIP]
>
>L’objet SWF et la balise `<video>` sont imbriqués dans la balise `<DIV>` parente.

