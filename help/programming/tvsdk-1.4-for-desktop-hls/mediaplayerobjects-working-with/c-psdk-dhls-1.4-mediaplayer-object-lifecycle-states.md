---
description: À partir du moment où vous créez l’instance MediaPlayer jusqu’au moment où vous l’arrêtez (réutilisez ou supprimez), cette instance effectue une série de transitions entre les états.
title: Cycle de vie de l’objet MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Cycle de vie de l’objet MediaPlayer{#mediaplayer-object-lifecycle}

À partir du moment où vous créez l’instance MediaPlayer jusqu’au moment où vous l’arrêtez (réutilisez ou supprimez), cette instance effectue une série de transitions entre les états.

Certaines opérations ne sont autorisées que lorsque le lecteur se trouve dans un état particulier. Par exemple, en appelant `play` dans IDLE n’est pas autorisé. Vous ne pouvez appeler cet état qu’une fois que le lecteur a atteint l’état PRÉPARÉ.

Pour utiliser les états :

* Vous pouvez récupérer l’état actuel de la variable `MediaPlayer` en utilisant l’objet `MediaPlayer.status` .

  ```
  function get status():String;
  ```

* La liste des états est définie dans la section `MediaPlayer.PlayerStatus`.

Diagramme de transition d’état pour le cycle de vie d’un `MediaPlayer` instance :
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-flash-1_2_web.png)

Le tableau suivant fournit des détails supplémentaires :

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <span class="codeph"> MediaPlayerStatus </span> </th> 
   <th colname="col2" class="entry"> Se produit lorsque </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> IDLE </span> </td> 
   <td colname="col2"> <p> Votre application a demandé un nouveau lecteur multimédia en instanciant <span class="codeph"> MediaPlayer </span>. Le lecteur nouvellement créé attend que vous souhaitiez spécifier un élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALISATION </span> </td> 
   <td colname="col2"> <p>Votre application appelée <span class="codeph"> MediaPlayer.replaceCurrentResource </span>et que le lecteur multimédia se charge. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALIZED </span> </td> 
   <td colname="col2"> <p>TVSDK a correctement défini l’élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PRÉPARATION </span> </td> 
   <td colname="col2"> <p>Votre application appelée <span class="codeph"> MediaPlayer.prepareToPlay </span>. Le lecteur multimédia charge l’élément du lecteur multimédia et les ressources associées. </p> <p>Conseil : Une mise en mémoire tampon du média principal peut se produire. </p> <p>TVSDK prépare le flux multimédia et tente d’effectuer la résolution des publicités et l’insertion de publicités (si activé). </p> <p>Conseil : Pour définir l’heure de début sur une valeur non nulle, appelez <span class="codeph"> prepareToPlay(startTime) </span> en millisecondes. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PRÉPARÉ </span> </td> 
   <td colname="col2"> <p>Le contenu est préparé et les publicités ont été insérées dans la chronologie ou la procédure publicitaire a échoué. La mise en mémoire tampon ou la lecture peuvent commencer. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> LECTURE </span> </td> 
   <td colname="col2"> <p>Votre application a appelé <span class="codeph"> play </span>, donc TVSDK tente de lire la vidéo. Une mise en mémoire tampon peut se produire avant la lecture de la vidéo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PAUSED </span> </td> 
   <td colname="col2"> <p>Lorsque votre application lit et met en pause le média, le lecteur multimédia passe de l’état à l’état LECTURE. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RECHERCHE </span> </td> 
   <td colname="col2"> <p>Le lecteur multimédia recherche la position correcte en pause ou en lecture. Pour déterminer quand la recherche a commencé ou s’est terminée, écoutez le <span class="codeph"> SeekEvent.SEEK_BEGIN </span> et <span class="codeph"> SeekEvent.SEEK_END </span> événements . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> TERMINÉ </span> </td> 
   <td colname="col2"> <p>Le lecteur a atteint la fin de la diffusion et la lecture s’est arrêtée. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PUBLIÉ </span> </td> 
   <td colname="col2"> <p>Votre application a publié le lecteur multimédia, qui libère également toutes les ressources associées. Vous ne pouvez plus utiliser cette instance. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> ERROR </span> </td> 
   <td colname="col2"> <p>Une erreur s’est produite pendant le processus. Une erreur peut également affecter les actions suivantes de votre application. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Vous pouvez utiliser l’état pour fournir des commentaires sur le processus (par exemple, un compteur en attendant le changement d’état suivant) ou pour passer à l’étape suivante de la lecture du média, par exemple en attendant le statut approprié avant d’appeler la méthode suivante.
