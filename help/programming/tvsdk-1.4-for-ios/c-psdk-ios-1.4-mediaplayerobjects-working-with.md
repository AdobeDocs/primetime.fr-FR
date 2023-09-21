---
description: L’objet PTMediaPlayer représente votre lecteur multimédia. Un PTMediaPlayerItem représente du contenu audio ou vidéo sur votre lecteur.
title: Utilisation d’objets MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Utilisation d’objets MediaPlayer{#work-with-mediaplayer-objects}

L’objet PTMediaPlayer représente votre lecteur multimédia. Un PTMediaPlayerItem représente du contenu audio ou vidéo sur votre lecteur.

## À propos de la classe MediaPlayerItem {#section_B6F36C0462644F5C932C8AA2F6827071}

Une fois la ressource multimédia chargée, TVSDK crée une instance de la fonction `PTMediaPlayerItem` pour fournir un accès à cette ressource.

La variable `PTMediaPlayer` résout la ressource multimédia, charge le fichier de manifeste associé et analyse le manifeste. Il s’agit de la partie asynchrone du processus de chargement des ressources. La variable `PTMediaPlayerItem` est générée une fois la ressource résolue, et cette instance est une version résolue d’une ressource multimédia. TVSDK permet d’accéder au `PTMediaPlayerItem` instance par `PTMediaPlayer.currentItem`.

>[!TIP]
>
>Vous devez attendre que la ressource soit chargée avant d’accéder à l’élément du lecteur multimédia.

## Cycle de vie de l’objet MediaPlayer {#section_D87EF7FBC7B442BDBE825156DC2C1CCF}

À partir du moment où vous créez le `PTMediaPlayer` au moment où vous l’arrêtez (réutilisez ou supprimez), cette instance effectue une série de transitions d’un état à un autre.

Certaines opérations ne sont autorisées que lorsque le lecteur se trouve dans un état particulier. Par exemple, en appelant `play` in `PTMediaPlayerStatusCreated` n’est pas autorisé. Vous ne pouvez appeler cet état qu’une fois que le lecteur a atteint l’événement `PTMediaPlayerStatusReady` statut.

Pour utiliser les états :

* Vous pouvez récupérer l’état actuel de l’objet MediaPlayer avec `PTMediaPlayer.status`.
* La liste des états est définie dans la section `PTMediaPlayerStatus`.

Diagramme de transition d’état pour le cycle de vie d’une instance MediaPlayer :
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
   <td colname="col2"> <p>Votre application a demandé un nouveau lecteur multimédia en appelant <span class="codeph"> playerWithMediaPlayerItem</span>. Le lecteur nouvellement créé attend que vous souhaitiez spécifier un élément du lecteur multimédia. Il s’agit de l’état initial du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing</span> </p> </td> 
   <td colname="col2"> <p>Vos appels d’application <span class="codeph"> PTMediaPlayer.replaceCurrentItemWithPlayerItem</span>et que le lecteur multimédia se charge. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusInitialized</span> </p> </td> 
   <td colname="col2"> <p>TVSDK a correctement défini l’élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusReady</span> </p> </td> 
   <td colname="col2"> <p>Le contenu est préparé et les publicités ont été insérées dans la chronologie ou la procédure publicitaire a échoué. La mise en mémoire tampon ou la lecture peuvent commencer. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPlaying</span> </p> </td> 
   <td colname="col2"> <p>Votre application a appelé <span class="codeph"> play</span>, donc TVSDK tente de lire la vidéo. Une mise en mémoire tampon peut se produire avant la lecture de la vidéo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPaused</span> </p> </td> 
   <td colname="col2"> <p>Lorsque votre application lit et met en pause le média, le lecteur multimédia se déplace entre cet état et <span class="codeph"> PTMediaPlayerStatusPlaying</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCompleted</span> </p> </td> 
   <td colname="col2"> <p>Le lecteur a atteint la fin de la diffusion et la lecture s’est arrêtée. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusStoppé</span> </p> </td> 
   <td colname="col2"> <p>Votre application a publié le lecteur multimédia, qui libère également toutes les ressources associées. Vous ne pouvez plus utiliser cette instance. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusError</span> </p> </td> 
   <td colname="col2"> <p>Une erreur s’est produite pendant le processus. Une erreur peut également affecter les actions suivantes de votre application. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Vous pouvez utiliser l’état pour fournir des commentaires sur le processus (par exemple, un compteur en attendant le changement d’état suivant) ou pour passer à l’étape suivante de la lecture du média, par exemple en attendant le statut approprié avant d’appeler la méthode suivante.
