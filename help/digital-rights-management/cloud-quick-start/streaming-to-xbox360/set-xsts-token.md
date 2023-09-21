---
title: Définition du jeton XSTS dans votre lecteur
description: Définition du jeton XSTS dans votre lecteur
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---


# Définition du jeton XSTS dans votre lecteur{#set-the-xsts-token-in-your-player}

Dans Xbox360, vous définissez le jeton de manière asynchrone en réponse au `MediaPlayer.RequestKeyAttribute` .

Définissez le jeton XSTS.

L’exemple d’application fourni avec votre logiciel indique comment définir le jeton XSTS dans votre lecteur. Voici le fragment de code approprié de l’exemple de lecteur :

```
   MediaPlayer mMediaPlayer;  
 
mMediaPlayer.RequestKeyAttribute += Player_RequestKeyAttribute;  
 
private void Player_RequestKeyAttribute(object sender, RequestKeyAttributeEventArgs args) {  
    string token = "";  
    // XBOX XSTS Token...  
    KeyAttribute keyAttribute = new KeyAttribute(System.Text.Encoding.UTF8.GetBytes(token), null);  
    mMediaPlayer.SetKeyAttribute(args.RequestIdentifier, keyAttribute);  
} 
```

