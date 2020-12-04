---
seo-title: Sélectionner les pistes audio
title: Sélectionner les pistes audio
uuid: a827f426-956b-4a5f-90ba-db12010aa7c7
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Sélectionnez les pistes audio{#select-the-audio-tracks}

Pour sélectionner des pistes audio à lier tardivement, implémentez [IAAConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IAAConfig.html).

| Pour... | Appeler... |
|---|---|
| Obtenir une liste de pistes AA disponibles | [getAudioTracks()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/AAManager.html#getAudioTracks()) |
| Obtenir la piste sélectionnée actuelle | [getSelectedAudioTrack()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/AAManager.html#getSelectedAudioTrack()) |
| Sélectionner une piste AA | [selectAlternateAudioTrack()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/AAManager.html#selectAlternateAudioTrack(int)) |

L’exemple de code suivant illustre comment l’implémentation de référence obtient les pistes audio du SDK TVSDK et affecte la piste sélectionnée à l’élément média associé :

```java
/** 
 * Displays a chooser dialog, allowing the user to select the desired 
 * alternate audio track. 
 */ 
private void displayAlternateAudioDialog() { 
    PrimetimeReference.logger.i(LOG_TAG + "#selectAlternateAudio", 
      "Displaying alternate audio chooser dialog."); 
    final int selectedAlternateAudio = aaManager.getSelectedAudioTrackIndex(); 
    if (selectedAlternateAudio != AAManagerOn.INVALID_AUDIO_TRACK) { 
        final String items[] = aaManager.getAudioTracks(); 
        new AlertDialog.Builder(getActivity()) 
          .setTitle(R.string.PlayerControlAADialogTitle) 
          .setSingleChoiceItems(items, selectedAlternateAudio, 
          new DialogInterface.OnClickListener() { 
              public void onClick(DialogInterface dialog, int whichButton) { 
                  boolean result =  
                    aaManager.selectAlternateAudioTrack(whichButton); 
                  if (result) { 
                      PrimetimeReference.logger.i(LOG_TAG 
                                                  + "#selectAlternateAudio", 
                                                  "Audio track selection successful"); 
                  } else { 
                      PrimetimeReference.logger.i(LOG_TAG 
                                            + "#selectAlternateAudio", 
                                            "Audio track selection failed"); 
                  } 
                  // Dismiss dialog. 
                  dialog.cancel(); 
              } 
          }).setNegativeButton(R.string.PlayerControlCCDialogCancel, 
                               new DialogInterface.OnClickListener() { 
              public void onClick(DialogInterface dialog, 
                                    int whichButton) { 
                                // Just cancel the dialog. 
              } 
          }).show(); 
 
    } else { 
        PrimetimeReference.logger.i(LOG_TAG + "#selectAlternateAudioFailed", 
                "Unable to detect the currently selected audio track."); 
        Toast.makeText(getActivity(), 
                "Unable to detect the currently selected audio track", 
                Toast.LENGTH_SHORT).show(); 
    } 
} 
```
