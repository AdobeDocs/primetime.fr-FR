---
description: 'null'
seo-description: 'null'
seo-title: Dépannage
title: Dépannage
uuid: 06b86067-1ff6-4b4e-922f-7f968260ba19
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Dépannage{#troubleshooting}

Voici quelques problèmes et solutions que vous pouvez rencontrer lors du déploiement.

* Si le message d’erreur suivant s’affiche :

   ```
   "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   Vérifiez que le mot de passe a été chiffré avec la `ScrambleUtil` classe.

* Si le message d’erreur suivant s’affiche :

   ```
   "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   Vérifiez que vous avez spécifié le mot de passe chiffré correct dans le fichier PFX.

* Si le message d’erreur suivant s’affiche :

   ```
   "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   Assurez-vous d’utiliser la classe scrambler de mot de passe *fournie avec l’implémentation* de référence. Cet utilitaire de scrambler est différent de celui fourni avec Adobe Primetime DRM Server for Protected Streaming.

