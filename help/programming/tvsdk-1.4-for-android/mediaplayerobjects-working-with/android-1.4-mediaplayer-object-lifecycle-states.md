---
description: Depuis le moment où vous créez l’instance MediaPlayer jusqu’au moment où vous l’arrêtez (réutilisez ou supprimez), cette instance complète une série de transitions entre les états.
title: Cycle de vie des objets MediaPlayer
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# Cycle de vie de l’objet MediaPlayer{#mediaplayer-object-lifecycle}

Depuis le moment où vous créez l’instance MediaPlayer jusqu’au moment où vous l’arrêtez (réutilisez ou supprimez), cette instance complète une série de transitions entre les états.

Certaines opérations ne sont autorisées que lorsque le lecteur se trouve dans un état particulier. Par exemple, l&#39;appel de `play` dans `IDLE` n&#39;est pas autorisé. Vous ne pouvez appeler cet état qu&#39;une fois que le lecteur a atteint l&#39;état `PREPARED`.

Pour travailler avec les états :

* Vous pouvez récupérer l’état actuel de l’objet `MediaPlayer` avec `MediaPlayer.getStatus`.

   ```java
   PlayerState getStatus() throws IllegalStateException;
   ```

* La liste des états est définie dans `MediaPlayer.PlayerState`.

Diagramme transition-état pour le cycle de vie d&#39;une instance `MediaPlayer` :
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

Le tableau suivant fournit des détails supplémentaires :

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> MediaPlayer.PlayerState </th> 
   <th colname="col2" class="entry"> Se produit lorsque </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> IDLE  </span> </td> 
   <td colname="col2"> <p>Votre application a demandé un nouveau lecteur multimédia en appelant <span class="codeph"> DefaultMediaPlayer.create </span>. Le nouveau lecteur attend que vous spécifiez un élément de lecteur multimédia. Il s'agit de l'état initial du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALISATION  </span> </td> 
   <td colname="col2"> <p>Votre application a appelé <span class="codeph"> MediaPlayer.replaceCurrentItem </span> et le lecteur multimédia est en cours de chargement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALISÉ  </span> </td> 
   <td colname="col2"> <p>TVSDK a correctement défini l’élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PRÉPARATION  </span> </td> 
   <td colname="col2"> <p>Votre application a appelé <span class="codeph"> MediaPlayer.prepareToPlay </span>. Le lecteur multimédia charge l’élément du lecteur multimédia et les ressources associées. </p> <p>Conseil :  Une mise en mémoire tampon du média principal peut se produire. </p> <p>TVSDK prépare le flux média et tente d’exécuter la résolution des publicités et l’insertion de publicités (si elle est activée). </p> <p>Conseil :  Pour définir l’heure du début sur une valeur non nulle, appelez <span class="codeph"> prepareToPlay(startTime) </span> avec l’heure en millisecondes. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PRÉPARÉ  </span> </td> 
   <td colname="col2"> <p>Le contenu est préparé et les publicités ont été insérées dans la chronologie ou la procédure publicitaire a échoué. La mise en mémoire tampon ou la lecture peuvent commencer. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> LECTURE  </span> </td> 
   <td colname="col2"> <p>Votre application a appelé <span class="codeph"> play </span>, de sorte que TVSDK tente de lire la vidéo. Une mise en mémoire tampon peut se produire avant la lecture de la vidéo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PAUSED  </span> </td> 
   <td colname="col2"> <p>Au fur et à mesure que votre application lit et met en pause le média, le lecteur multimédia se déplace entre cet état et la LECTURE. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> SUSPENDU  </span> </td> 
   <td colname="col2"> <p>Votre application a quitté la lecture, a arrêté le périphérique ou a changé d’application pendant la lecture ou la mise en pause du lecteur. Le lecteur multimédia a été suspendu et des ressources ont été libérées. Pour continuer, restaurez le lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> TERMINÉ  </span> </td> 
   <td colname="col2"> <p>Le lecteur a atteint la fin du flux et la lecture s’est arrêtée. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> LIBÉRÉ  </span> </td> 
   <td colname="col2"> <p>Votre application a publié le lecteur multimédia, qui libère également toutes les ressources associées. Vous ne pouvez plus utiliser cette instance </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> ERREUR  </span> </td> 
   <td colname="col2"> <p>Une erreur s'est produite pendant le processus. Une erreur peut également avoir une incidence sur les prochaines actions de votre application. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Vous pouvez utiliser l’état pour fournir des commentaires sur le processus (par exemple, un analyseur en attendant le changement d’état suivant) ou pour passer à l’étape suivante lors de la lecture du média, par exemple en attendant l’état approprié avant d’appeler la méthode suivante.

Par exemple :

```java
@Override 
public void onStateChanged(MediaPlayer.PlayerState state,  
                           MediaPlayerNotification notification) { 
   switch (state) { 
      // It is recommended that you call prepareToPlay() after receiving  
      // the INITIALIZED state. 
      case INITIALIZED: 
         _mediaPlayer.prepareToPlay(); 
         break; 
      case PREPARING: 
         showBufferingSpinner(); 
         break; 
      case PREPARED: 
         hideBufferingSpinner(); 
      ..... 
    } 
}
```

