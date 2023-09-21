---
title: Dépannage
description: Dépannage
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Dépannage {#troubleshooting}

Les problèmes courants et les solutions de déploiement répertoriés ci-dessous sont les suivants :

* Si l’erreur suivante s’affiche :

  ```
      "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
      javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
  ```

  Assurez-vous que le mot de passe est chiffré à l’aide du `ScrambleUtil` classe .

* Si l’erreur suivante s’affiche :

  ```
      "Unable to load credential from file.pfx -- possibly wrong password."
  ```

  Assurez-vous d’avoir spécifié le mot de passe chiffré correct pour le fichier PFX.

* Si l’erreur suivante s’affiche :

  ```
      "javax.crypto.BadPaddingException: Given final block not properly padded"
  ```

  Assurez-vous d’avoir utilisé la classe de scrambler de mot de passe fournie avec l’implémentation de référence (cet utilitaire de scrambler est différent de celui fourni avec l’Adobe® Access™ Server for Protected Streaming).
