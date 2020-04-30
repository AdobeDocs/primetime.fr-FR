---
seo-title: Dépannage
title: Dépannage
uuid: db76d6a4-c285-4d86-95a1-4f1a85ed3743
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Dépannage {#troubleshooting}

Vous trouverez ci-dessous la liste des problèmes courants et des solutions de déploiement :

* Si l’erreur suivante s’affiche :

   ```
       "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   Assurez-vous que le mot de passe est chiffré à l’aide de la `ScrambleUtil` classe fournie.

* Si l’erreur suivante s’affiche :

   ```
       "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   Assurez-vous d’avoir spécifié le mot de passe chiffré correct pour le fichier PFX.

* Si l’erreur suivante s’affiche :

   ```
       "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   Assurez-vous d’avoir utilisé la classe scrambler de mot de passe fournie avec l’implémentation de référence (cet utilitaire de scrambler est différent de celui fourni avec Adobe® Access™ Server for Protected Streaming).

