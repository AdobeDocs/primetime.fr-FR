---
title: Dépannage
description: Dépannage
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Dépannage{#troubleshooting}

Voici quelques problèmes et solutions que vous pouvez rencontrer lors du déploiement.

* Si le message d’erreur suivant s’affiche :

   ```
   "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   Assurez-vous que le mot de passe a été chiffré avec la classe `ScrambleUtil`.

* Si le message d’erreur suivant s’affiche :

   ```
   "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   Assurez-vous d’avoir spécifié le mot de passe chiffré correct dans le fichier PFX.

* Si le message d’erreur suivant s’affiche :

   ```
   "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   Assurez-vous d’utiliser la classe de scrambler de mot de passe *fournie avec l’implémentation de référence*. Cet utilitaire de scrambler est différent de celui fourni avec Adobe Primetime DRM Server pour la diffusion en flux continu protégée.

