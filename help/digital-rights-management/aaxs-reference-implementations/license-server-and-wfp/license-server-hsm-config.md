---
seo-title: Configuration HSM
title: Configuration HSM
uuid: 1cc5be99-c24c-4c1e-9348-fb69f96d8ca5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Configuration HSM {#hsm-configuration}

L’utilisation d’un HSM n’est pas obligatoire, mais elle est recommandée. L’implémentation de référence peut être configurée pour utiliser le fournisseur Sun PKCS11 pour la prise en charge HSM. Pour utiliser des informations d’identification sur un HSM, vous devez créer un fichier de configuration pour le fournisseur Sun PKCS11. Consultez la documentation de Sun pour plus d’informations. Pour vérifier que votre fichier de configuration HSM et Sun PKCS11 est correctement configuré, vous pouvez utiliser la commande suivante (keytool est installé avec le JDK Java) :

```
    keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
        -providerArg pkcs11.cfg -list
```

Si vos informations d’identification s’affichent dans la liste, le module HSM est correctement configuré.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Depuis Java 1.7, Sun Java 64 bits pour Windows ne prend pas en charge les interfaces PKCS11 requises par Adobe Access DRM pour communiquer avec les périphériques HSM. Si vous prévoyez d’utiliser un module HSM, utilisez une version 32 bits de Java ou utilisez un JDK qui prend en charge les interfaces PKCS11 complètes.

