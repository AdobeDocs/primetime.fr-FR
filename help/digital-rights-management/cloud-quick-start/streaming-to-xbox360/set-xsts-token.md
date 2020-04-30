---
description: 'null'
seo-description: 'null'
seo-title: Définition du jeton XSTS dans votre lecteur
title: Définition du jeton XSTS dans votre lecteur
uuid: 8995e029-deee-4e23-9cda-a50de8c4f2c0
translation-type: tm+mt
source-git-commit: b7f52b71bde1d7bf59ef51d4f6f90dfaa07e347b

---


# Définition du jeton XSTS dans votre lecteur{#set-the-xsts-token-in-your-player}

Dans Xbox360, vous définissez le jeton de manière asynchrone en réponse au `MediaPlayer.RequestKeyAttribute` événement.

Définissez le jeton XSTS.

L’exemple d’application fourni avec votre logiciel montre comment définir le jeton XSTS dans votre lecteur. Voici le fragment de code correspondant extrait du lecteur d’exemple :

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

