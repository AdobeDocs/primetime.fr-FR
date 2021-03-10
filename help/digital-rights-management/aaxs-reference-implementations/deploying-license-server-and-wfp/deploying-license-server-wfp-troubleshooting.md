---
title: Dépannage
description: Dépannage
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# Dépannage {#troubleshooting}

Vous trouverez ci-dessous la liste des problèmes courants et des solutions de déploiement :

* Si l’erreur suivante s’affiche :

   ```
       "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   Assurez-vous que le mot de passe est chiffré en utilisant la classe `ScrambleUtil` fournie.

* Si l’erreur suivante s’affiche :

   ```
       "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   Assurez-vous d’avoir spécifié le mot de passe chiffré correct pour le fichier PFX.

* Si l’erreur suivante s’affiche :

   ```
       "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   Assurez-vous d&#39;avoir utilisé la classe scrambler de mot de passe fournie avec la mise en oeuvre de référence (cet utilitaire de scrambler est différent de celui fourni avec le serveur Adobe® Access™ Server for Protected Streaming).

