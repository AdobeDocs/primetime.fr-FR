---
description: Il s’agit d’un exemple de création d’un bouton qui permet à un utilisateur de sélectionner un suivi de sous-titres non intégrés.
title: Exemple Autoriser les utilisateurs à modifier le suivi des sous-titres
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Exemple : permettre aux utilisateurs de modifier le suivi des sous-titres{#example-allow-users-to-change-the-caption-track}

Il s’agit d’un exemple de création d’un bouton qui permet à un utilisateur de sélectionner un suivi de sous-titres non intégrés.

1. Créez un bouton simple pour modifier le suivi des sous-titres.

   ```xml
      <Button 
     android:id="@+id/selectCC" 
     android:layout_width="wrap_content" 
     android:layout_height="wrap_content" 
     android:layout_alignParentBottom="true" 
     android:layout_alignParentRight="true" 
     android:layout_marginRight="10dp" 
     android:onClick="selectClosedCaptioningClick" 
     android:text="CC" /> 
   ```

1. Convertissez la liste des pistes de sous-titres disponibles en tableau de chaînes. Les suivis de sous-titres fermés qui comportent une activité (c’est-à-dire les canaux pour lesquels TVSDK a découvert des données) sont marqués en conséquence :

   ```java
   /** 
   * Converts the closed captions tracks to a string array. 
   * 
   * @return array of CC tracks 
   */ 
   private String[] getCCsAsArray() { 
       List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); 
       MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); 
       if (currentItem != null) { 
           List<ClosedCaptionsTrack> closedCaptionsTracks = 
             currentItem.getClosedCaptionsTracks(); 
           Iterator<ClosedCaptionsTrack> iterator = closedCaptionsTracks.iterator(); 
           while (iterator.hasNext()) { 
               ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); 
               String isActive = closedCaptionsTrack.isActive() ? " (" + getString(R.string.active)+ ")" : ""; 
               closedCaptionsTracksAsStrings.add(closedCaptionsTrack.getName() + isActive); 
           } 
       } 
       return closedCaptionsTracksAsStrings.toArray(new 
       String[closedCaptionsTracksAsStrings.size()]); 
   } 
   ```

1. Lorsque l’utilisateur clique sur le bouton, affichez une boîte de dialogue qui répertorie tous les suivi CC par défaut.

   ```java
      public void selectClosedCaptioningClick(View view) { 
       Log.i(LOG_TAG + "#selectClosedCaptions", "Displaying closed captions chooser dialog."); 
       final String items[] = getCCsAsArray(); 
       final AlertDialog.Builder ab = new AlertDialog.Builder(this); 
       ab.setTitle(R.string.PlayerControlCCDialogTitle); 
       ab.setSingleChoiceItems(items, selectedClosedCaptionsIndex, new DialogInterface.OnClickListener() { 
           public void onClick(DialogInterface dialog, int whichButton) { 
               // Select the new closed captioning track. 
               MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); 
               ClosedCaptionsTrack desiredClosedCaptionsTrack = currentItem.getClosedCaptionsTracks().get(whichButton); 
               boolean result = currentItem.selectClosedCaptionsTrack(desiredClosedCaptionsTrack); 
               if (result) { 
                   selectedClosedCaptionsIndex = whichButton; 
               } 
               // Dismiss dialog. 
               dialog.cancel(); 
           } 
       }).setNegativeButton(R.string.PlayerControlCCDialogCancel, new DialogInterface.OnClickListener() { 
           public void onClick(DialogInterface dialog, int whichButton) { 
           // Just cancel the dialog. 
           } 
       }); 
       ab.show(); 
   } 
   ```
