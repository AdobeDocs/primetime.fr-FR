---
description: L’état du lecteur multimédia détermine les actions légales.
title: Cycle de vie et états de l’objet MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Cycle de vie et états de l’objet MediaPlayer{#lifecycle-and-statuses-of-the-mediaplayer-object}

L’état du lecteur multimédia détermine les actions légales.

Pour utiliser les états du lecteur multimédia :

* Vous pouvez récupérer l’état actuel de la variable `MediaPlayer` avec `MediaPlayer.getStatus()`.

* La liste des états est définie dans la variable [MediaPlayerStatus](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/com/adobe/mediacore/MediaPlayerStatus.html) enum.

Diagramme de transition d’état pour le cycle de vie d’un `MediaPlayer` instance :

<!--<a id="fig_A6425F24C7734DC681D992859D2A6743"></a>-->

![](assets/media_player_statuses.png)

Le tableau suivant fournit des détails sur le cycle de vie et les états du lecteur multimédia :

<table id="table_82757A0043EB4AACA474E6B30326A6B7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> État </th> 
   <th colname="col2" class="entry"> Se produit lorsque </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> IDLE </td> 
   <td colname="col2"> <p>État initial du lecteur multimédia. Le lecteur est créé et attend que vous définissiez un élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALISATION </td> 
   <td colname="col2"> <p>Vos appels d’application <span class="codeph"> MediaPlayer.replaceCurrentItem() </span>. </p> <p>L’élément du lecteur multimédia est en cours de chargement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALIZED </td> 
   <td colname="col2"> <p>TVSDK a correctement défini l’élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> PRÉPARATION </td> 
   <td colname="col2"> <p>Vos appels d’application <span class="codeph"> MediaPlayer.prepareToPlay() </span>. Le lecteur multimédia charge l’élément du lecteur multimédia et toutes les ressources associées. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> PRÉPARÉ </td> 
   <td colname="col2"> <p>TVSDK a préparé le flux multimédia et a tenté d’effectuer la résolution des publicités et l’insertion de publicités (si activé). Le contenu est préparé et les publicités ont été insérées dans la chronologie ou la procédure publicitaire a échoué. </p> <p>La mise en mémoire tampon ou la lecture peuvent commencer. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> LECTURE/MISE EN PAUSE </td> 
   <td colname="col2"> <p>Lorsque l’application lit et met en pause le média, le lecteur multimédia se déplace entre ces états. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> SUSPENDU </td> 
   <td colname="col2"> <p>Si l’application quitte la lecture, arrête l’appareil ou change d’application pendant la lecture ou la mise en pause du lecteur, le lecteur multimédia est suspendu et les ressources sont libérées. </p> <p>Appel <span class="codeph"> MediaPlayer.restore() </span> renvoie le lecteur à l’état dans lequel il se trouvait avant d’être SUSPENDU. L’exception est que si le lecteur EFFECTUE UNE RECHERCHE lors de l’appel de la suspension, le lecteur est EN PAUSE, puis SUSPENDU. </p> <p>Important :  <p>Gardez à l’esprit les informations suivantes : 
      <ul id="ul_1B21668994D1474AAA0BE839E0D69B00"> 
       <li id="li_08459A3AB03C45588D73FA162C27A56C">La variable <span class="codeph"> MediaPlayer </span> appels automatiques <span class="codeph"> suspendre </span> uniquement lorsque l’objet de surface utilisé par la fonction <span class="codeph"> MediaPlayerView </span> est détruite. </li> 
       <li id="li_B9926AA2E7B9441490F37D24AE2678A1">La variable <span class="codeph"> MediaPlayer </span> appels automatiques <span class="codeph"> restore() </span> uniquement lorsqu’un nouvel objet de surface utilisé par l’objet <span class="codeph"> MediaPlayerView </span> est créée. </li> 
      </ul> </p> </p> <p>Si vous souhaitez toujours que la lecture soit mise en pause lors de la restauration du MediaPlayer, faites appel à votre application <span class="codeph"> MediaPlayer.pause() </span> dans l’activité Android <span class="codeph"> onPause() </span> . </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> TERMINER </td> 
   <td colname="col2"> <p>Le lecteur a atteint la fin de la diffusion et la lecture s’est arrêtée. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> PUBLIÉ </td> 
   <td colname="col2"> <p>Votre application a publié le lecteur multimédia, qui libère également toutes les ressources associées. Vous ne pouvez plus utiliser cette instance. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ERROR </td> 
   <td colname="col2"> <p>Une erreur s’est produite pendant le processus. Une erreur peut également affecter ce que l’application peut faire ensuite. Pour plus d’informations, voir <a href="../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-error-handling-set-up.md" format="dita" scope="local"> Configuration de la gestion des erreurs </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Vous pouvez utiliser l’état pour fournir des commentaires sur le processus, par exemple, un compteur en attendant la prochaine modification de l’état, ou suivre les étapes suivantes de lecture du média, telles que l’attente du statut approprié avant d’appeler la méthode suivante.

Par exemple :

```java
mediaPlayer.addEventListener(MediaPlayerEvent STATUS_CHANGED, new StatusChangeEventListener() { 
    @Override  
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        switch(event.getStatus()) { 
            case INITIALIZED: 
                mediaPlayer.prepareToPlay(); 
                break; 
            case PREPARING: 
                showBufferingSpinner(); 
                break; 
            case PREPARED: 
                hideBufferingSpinner(); 
                mediaPlayer.play(); 
                break; 
            ...                
        } 
        ... 
    } 
}); 
```
