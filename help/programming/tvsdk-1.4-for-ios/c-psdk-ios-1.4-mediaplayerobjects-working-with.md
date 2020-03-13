---
description: L’objet PTMediaPlayer représente votre lecteur multimédia. Un objet PTMediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.
seo-description: L’objet PTMediaPlayer représente votre lecteur multimédia. Un objet PTMediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.
seo-title: Utilisation d’objets MediaPlayer
title: Utilisation d’objets MediaPlayer
uuid: eba26ad7-8c9a-4703-af32-1dfb928f6b67
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Utilisation d’objets MediaPlayer{#work-with-mediaplayer-objects}

L’objet PTMediaPlayer représente votre lecteur multimédia. Un objet PTMediaPlayerItem représente l’audio ou la vidéo sur votre lecteur.

## A propos de la classe MediaPlayerItem {#section_B6F36C0462644F5C932C8AA2F6827071}

Une fois qu’une ressource multimédia a été chargée, TVSDK crée une instance de la `PTMediaPlayerItem` classe pour fournir un accès à cette ressource.

Le `PTMediaPlayer` programme résout la ressource multimédia, charge le fichier manifeste associé et analyse le manifeste. Il s’agit de la partie asynchrone du processus de chargement des ressources. L’ `PTMediaPlayerItem` instance est générée une fois la ressource résolue, et cette instance est une version résolue d’une ressource multimédia. TVSDK permet d’accéder à l’ `PTMediaPlayerItem` instance nouvellement créée par le biais `PTMediaPlayer.currentItem`.

>[!TIP]
>
>Vous devez attendre que la ressource soit chargée correctement avant d’accéder à l’élément du lecteur multimédia.

## Cycle de vie de l’objet MediaPlayer {#section_D87EF7FBC7B442BDBE825156DC2C1CCF}

Du moment où vous créez l’ `PTMediaPlayer` instance au moment où vous l’arrêtez (réutilisez ou supprimez), cette instance termine une série de  d’un état à un autre.

Certaines opérations ne sont autorisées que lorsque le lecteur se trouve dans un état particulier. Par exemple, l’appel `play` à `PTMediaPlayerStatusCreated` n’est pas autorisé. Vous ne pouvez appeler cet état qu’une fois que le lecteur a atteint l’ `PTMediaPlayerStatusReady` état.

Pour utiliser les états :

* Vous pouvez récupérer l’état actuel de l’objet MediaPlayer avec `PTMediaPlayer.status`.
* Le  des états est défini dans `PTMediaPlayerStatus`.

Diagramme Etat- pour le cycle de vie d’une instance MediaPlayer :
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-ios2_web.png)

Le tableau suivant fournit des détails supplémentaires :

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> PTMediaPlayerStatus </th> 
   <th colname="col2" class="entry"> Se produit lorsque </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCreated</span> </p> </td> 
   <td colname="col2"> <p>Votre application a demandé un nouveau lecteur multimédia en appelant <span class="codeph"> playerWithMediaPlayerItem</span>. Le lecteur nouvellement créé attend que vous spécifiez un élément du lecteur multimédia. Il s’agit de l’état initial du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing</span> </p> </td> 
   <td colname="col2"> <p>Votre application appelle <span class="codeph"> PTMediaPlayer.replaceCurrentItemWithPlayerItem</span>et le lecteur multimédia est en cours de chargement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusInitialized</span> </p> </td> 
   <td colname="col2"> <p>Le kit TVSDK a correctement défini l’élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusReady</span> </p> </td> 
   <td colname="col2"> <p>Le contenu est préparé et les publicités ont été insérées dans la chronologie, ou la procédure publicitaire a échoué. La mise en mémoire tampon ou la lecture peuvent commencer. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPlaying</span> </p> </td> 
   <td colname="col2"> <p>Votre application a appelé <span class="codeph"> play</span>, donc TVSDK essaie de lire la vidéo. Une mise en mémoire tampon peut se produire avant la lecture de la vidéo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPaused</span> </p> </td> 
   <td colname="col2"> <p>Lorsque votre application est lue et met en pause le média, le lecteur multimédia se déplace entre cet état et <span class="codeph"> PTMediaPlayerStatusPlaying</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCompleted</span> </p> </td> 
   <td colname="col2"> <p>Le lecteur a atteint la fin du flux et la lecture s’est arrêtée. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusArrêté</span> </p> </td> 
   <td colname="col2"> <p>Votre application a publié le lecteur multimédia, qui libère également toutes les ressources associées. Vous ne pouvez plus utiliser cette instance </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusError</span> </p> </td> 
   <td colname="col2"> <p>Une erreur s'est produite pendant le processus. Une erreur peut également affecter les actions suivantes de votre application. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Vous pouvez utiliser l’état pour fournir des commentaires sur le processus (par exemple, un compteur en attendant le changement d’état suivant) ou pour passer à l’étape suivante lors de la lecture du média, par exemple en attendant l’état approprié avant d’appeler la méthode suivante.

