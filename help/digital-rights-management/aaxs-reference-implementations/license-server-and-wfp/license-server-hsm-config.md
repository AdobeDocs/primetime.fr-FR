---
title: Configuration HSM
description: Configuration HSM
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Configuration HSM {#hsm-configuration}

L’utilisation d’un HSM n’est pas obligatoire, mais elle est recommandée. L’implémentation de référence peut être configurée pour utiliser le fournisseur Sun PKCS11 pour la prise en charge HSM. Pour utiliser des informations d’identification sur un HSM, vous devez créer un fichier de configuration pour le fournisseur Sun PKCS11. Consultez la documentation de Sun pour plus d’informations. Pour vérifier que votre fichier de configuration HSM et Sun PKCS11 est correctement configuré, vous pouvez utiliser la commande suivante (keytool est installé avec le JDK Java) :

```
    keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
        -providerArg pkcs11.cfg -list
```

Si vos informations d’identification s’affichent dans la liste, le module HSM est correctement configuré.

>[!NOTE]
>
>Depuis Java 1.7, Sun Java 64 bits pour Windows ne prend pas en charge les interfaces PKCS11 dont Adobe Access DRM a besoin pour communiquer avec les périphériques HSM. Si vous prévoyez d’utiliser un module HSM, utilisez une version 32 bits de Java ou utilisez un JDK qui prend en charge les interfaces PKCS11 complètes.

