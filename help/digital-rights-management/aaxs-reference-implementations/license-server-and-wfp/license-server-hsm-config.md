---
title: Configuration HSM
description: Configuration HSM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Configuration HSM {#hsm-configuration}

L’utilisation d’un HSM n’est pas requise, mais elle est recommandée. L’implémentation de référence peut être configurée pour utiliser le fournisseur Sun PKCS11 pour la prise en charge HSM. Pour utiliser des informations d’identification sur un HSM, vous devez créer un fichier de configuration pour le fournisseur Sun PKCS11. Pour plus d’informations, consultez la documentation de Sun . Pour vérifier que votre fichier de configuration HSM et Sun PKCS11 sont correctement configurés, vous pouvez utiliser la commande suivante (keytool est installé avec le JDK Java) :

```
    keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
        -providerArg pkcs11.cfg -list
```

Si vos informations d’identification s’affichent dans la liste, le module HSM est correctement configuré.

>[!NOTE]
>
>Depuis Java 1.7, Sun Java 64 bits pour Windows ne prend pas en charge les interfaces PKCS11 dont Adobe Access DRM a besoin pour communiquer avec les périphériques HSM. Si vous prévoyez d’utiliser un HSM, utilisez une version 32 bits de Java ou utilisez un JDK qui prend en charge les interfaces PKCS11 complètes.
