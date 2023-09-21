---
title: Dépannage
description: Dépannage
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Dépannage{#troubleshooting}

Voici quelques problèmes et solutions que vous pouvez rencontrer lors du déploiement.

* Si le message d&#39;erreur suivant s&#39;affiche :

  ```
  "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
      javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
  ```

  Assurez-vous que le mot de passe a été chiffré avec la variable `ScrambleUtil` classe .

* Si le message d&#39;erreur suivant s&#39;affiche :

  ```
  "Unable to load credential from file.pfx -- possibly wrong password."
  ```

  Assurez-vous d’avoir spécifié le mot de passe chiffré correct dans le fichier PFX.

* Si le message d&#39;erreur suivant s&#39;affiche :

  ```
  "javax.crypto.BadPaddingException: Given final block not properly padded"
  ```

  Assurez-vous d’utiliser la classe de scrambler de mot de passe *fourni avec l’implémentation de référence*. Cet utilitaire de script est différent de celui fourni avec le serveur Adobe Primetime DRM pour la diffusion en continu protégée.
