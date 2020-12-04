---
description: L’état du lecteur de médias détermine quelles actions sont légales.
seo-description: L’état du lecteur de médias détermine quelles actions sont légales.
seo-title: Cycle de vie et états de l’objet MediaPlayer
title: Cycle de vie et états de l’objet MediaPlayer
uuid: a0eb27c8-180b-4c56-926f-59fa3bcef032
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Cycle de vie et états de l’objet MediaPlayer {#lifecycle-and-statuses-of-the-mediaplayer-object}

L’état du lecteur de médias détermine quelles actions sont légales.

Pour utiliser les états du lecteur multimédia :

* Vous pouvez récupérer l’état actuel de l’objet `MediaPlayer` avec `MediaPlayer.getStatus()`.

* La liste des états est définie dans l&#39;énumération [MediaPlayerStatus](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/com/adobe/mediacore/MediaPlayerStatus.html).

Diagramme transition-état pour le cycle de vie d&#39;une instance `MediaPlayer` :
<!--<a id="fig_A6425F24C7734DC681D992859D2A6743"></a>-->

![](assets/media_player_statuses.png)

Le tableau suivant fournit des détails sur le cycle de vie et les états du lecteur de médias :

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
   <td colname="col2"> <p>Statut initial du lecteur multimédia. Le lecteur est créé et attend que vous spécifiez un élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALISATION </td> 
   <td colname="col2"> <p>Votre application appelle <span class="codeph"> MediaPlayer.replaceCurrentItem() </span>. </p> <p>L’élément du lecteur multimédia est en cours de chargement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALISÉ </td> 
   <td colname="col2"> <p>TVSDK a correctement défini l’élément du lecteur multimédia. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> PRÉPARATION </td> 
   <td colname="col2"> <p>Votre application appelle <span class="codeph"> MediaPlayer.prepareToPlay() </span>. Le lecteur multimédia charge l’élément du lecteur multimédia et les ressources associées. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> PRÉPARÉ </td> 
   <td colname="col2"> <p>TVSDK a préparé le flux média et a tenté d’exécuter la résolution des publicités et l’insertion de publicités (si elle est activée). Le contenu est préparé et les publicités ont été insérées dans la chronologie ou la procédure publicitaire a échoué. </p> <p>La mise en mémoire tampon ou la lecture peuvent commencer. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> LECTURE/SUSPENSION </td> 
   <td colname="col2"> <p>Au fur et à mesure que l’application lit et met en pause le média, le lecteur de médias passe d’un état à l’autre. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> SUSPENDU </td> 
   <td colname="col2"> <p>Si l’application quitte la lecture, arrête le périphérique ou change d’application pendant la lecture ou la mise en pause, le lecteur multimédia est suspendu et les ressources libérées. </p> <p>L'appel à <span class="codeph"> MediaPlayer.restore() </span> renvoie le lecteur à l'état dans lequel il se trouvait avant sa SUSPENSION. L’exception est que si le lecteur RECHERCHE lorsqu’il est suspendu est appelé, le lecteur est EN PAUSE, puis SUSPENDU. </p> <p>Important :  <p>Rappelez-vous des informations suivantes : 
      <ul id="ul_1B21668994D1474AAA0BE839E0D69B00"> 
       <li id="li_08459A3AB03C45588D73FA162C27A56C"><span class="codeph"> MediaPlayer </span> appelle automatiquement <span class="codeph"> suspendre </span> uniquement lorsque l'objet de surface utilisé par <span class="codeph"> MediaPlayerView </span> est détruit. </li> 
       <li id="li_B9926AA2E7B9441490F37D24AE2678A1"><span class="codeph"> MediaPlayer </span> n'appelle automatiquement <span class="codeph"> restore() </span> que lorsqu'un nouvel objet de surface utilisé par <span class="codeph"> MediaPlayerView </span> est créé. </li> 
      </ul> </p> </p> <p>Si vous souhaitez toujours que la lecture soit interrompue lorsque MediaPlayer est restauré, faites appel à l’application <span class="codeph"> MediaPlayer.pause() </span> dans la méthode <span class="codeph"> onPause() </span> de l’Activité Android. </p> </td> 
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
   <td colname="col2"> <p>Une erreur s'est produite pendant le processus. Une erreur peut également avoir une incidence sur ce que l’application peut faire ensuite. Pour plus d'informations, voir <a href="../../../tvsdk-2.7-for-android/content-playback-options/t-psdk-android-2.7-error-handling-set-up.md#set-up-error-handling" format="dita" scope="local"> Configuration de la gestion des erreurs </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>Vous pouvez utiliser l’état pour fournir des commentaires sur le processus, par exemple, un analyseur en attendant la prochaine modification de l’état, ou suivre les étapes suivantes de lecture du média, par exemple en attendant l’état approprié avant d’appeler la méthode suivante.

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

