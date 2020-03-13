---
description: Le statut du lecteur multimédia détermine les actions légales.
seo-description: Le statut du lecteur multimédia détermine les actions légales.
seo-title: Cycle de vie et états de l’objet MediaPlayer
title: Cycle de vie et états de l’objet MediaPlayer
uuid: a2866f84-a722-46ed-b4cb-36664db5be82
translation-type: tm+mt
source-git-commit: 56dc79e5b4df11ff730d7d8f23dea8d0f4712077

---


# Cycle de vie et états de l’objet MediaPlayer{#lifecycle-and-statuses-of-the-mediaplayer-object}

Le statut du lecteur multimédia détermine les actions légales.

Pour utiliser les états du lecteur multimédia :

* Vous pouvez récupérer l’état actuel de l’ `MediaPlayer` objet avec `MediaPlayer.getStatus()`.

* Le d’états est défini dans l’enum [MediaPlayerStatus](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/com/adobe/mediacore/MediaPlayerStatus.html) .

Diagramme État- pour le cycle de vie d’une `MediaPlayer` instance :

<!--<a id="fig_A6425F24C7734DC681D992859D2A6743"></a>-->

![](assets/media_player_statuses.png)

Le tableau suivant fournit des détails sur le cycle de vie et les états du lecteur multimédia :

<table id="table_82757A0043EB4AACA474E6B30326A6B7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Statut </th> 
   <th colname="col2" class="entry"> Se produit lorsque </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> IDLE </td> 
   <td colname="col2"> <p>Statut initial du lecteur multimédia. Le lecteur est créé et vous attend pour spécifier un élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALISATION </td> 
   <td colname="col2"> <p>Votre application appelle <span class="codeph"> MediaPlayer.replaceCurrentItem() </span>. </p> <p>L’élément du lecteur multimédia est en cours de chargement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALISÉ </td> 
   <td colname="col2"> <p>Le kit TVSDK a correctement défini l’élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> PRÉPARATION </td> 
   <td colname="col2"> <p>Votre application appelle <span class="codeph"> MediaPlayer.prepareToPlay() </span>. Le lecteur multimédia charge l’élément du lecteur multimédia et les ressources associées. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> PRÉPARÉ </td> 
   <td colname="col2"> <p>TVSDK a préparé le flux média et a tenté d’exécuter la résolution et l’insertion de publicités (si elle est activée). Le contenu est préparé et les publicités ont été insérées dans la chronologie ou la procédure publicitaire a échoué. </p> <p>La mise en mémoire tampon ou la lecture peuvent commencer. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> LECTURE/SUSPENDU </td> 
   <td colname="col2"> <p>Lorsque l’application est lue et met en pause le média, le lecteur de médias passe d’un état à l’autre. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> SUSPENDU </td> 
   <td colname="col2"> <p>Si l’application quitte la lecture, arrête le périphérique ou change d’application pendant la lecture ou la mise en pause, le lecteur multimédia est suspendu et les ressources libérées. </p> <p>L’appel de <span class="codeph"> MediaPlayer.restore() </span> renvoie le lecteur à l’état dans lequel il se trouvait avant sa SUSPENSION. L’exception est que si le lecteur RECHERCHE lors de l’appel de la suspension, le lecteur est EN PAUSE, puis SUSPENDU. </p> <p>Important :  <p>Tenez compte des informations suivantes : 
      <ul id="ul_1B21668994D1474AAA0BE839E0D69B00"> 
       <li id="li_08459A3AB03C45588D73FA162C27A56C">Le <span class="codeph"> lecteur multimédia </span> appelle automatiquement <span class="codeph"> la suspension uniquement lorsque l’objet de surface utilisé par </span> MediaPlayerView <span class="codeph"> </span> est détruit. </li> 
       <li id="li_B9926AA2E7B9441490F37D24AE2678A1">Le <span class="codeph"> lecteur multimédia </span> appelle <span class="codeph"> automatiquement restore() uniquement lorsqu’un nouvel objet de surface utilisé par </span> MediaPlayerView <span class="codeph"> </span> est créé. </li> 
      </ul> </p> </p> <p>Si vous souhaitez toujours que la lecture soit interrompue lorsque le lecteur multimédia est restauré, faites appel à <span class="codeph"> MediaPlayer.pause() </span> dans le Android   la <span class="codeph"> </span> méthode onPause(). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> TERMINÉ </td> 
   <td colname="col2"> <p>Le lecteur a atteint la fin du flux et la lecture s’est arrêtée. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> LIBÉRÉ </td> 
   <td colname="col2"> <p>Votre application a publié le lecteur multimédia, qui libère également toutes les ressources associées. Vous ne pouvez plus utiliser cette instance. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ERREUR </td> 
   <td colname="col2"> <p>Une erreur s'est produite pendant le processus. Une erreur peut également affecter les actions de l’application. Pour plus d’informations, voir <a href="../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-error-handling-set-up.md" format="dita" scope="local"> Configuration de la gestion des erreurs </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Vous pouvez utiliser l’état pour fournir des commentaires sur le processus, par exemple, un compteur en attendant le changement d’état suivant, ou suivre les étapes suivantes de lecture du média, comme l’attente du statut approprié avant d’appeler la méthode suivante.

Par exemple :

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
