---
description: Vous pouvez configurer l’implémentation de référence avec le fournisseur Sun PKCS#11 qui prend en charge HSM. Bien que l’utilisation d’un HSM ne soit pas requise, elle est recommandée.
title: Configuration HSM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configuration HSM{#hsm-configuration}

Vous pouvez configurer l’implémentation de référence avec le fournisseur Sun PKCS#11 qui prend en charge HSM. Bien que l’utilisation d’un HSM ne soit pas requise, elle est recommandée.

Pour utiliser des informations d’identification sur un HSM, vous devez créer un fichier de configuration pour le fournisseur Sun PKCS#11. Pour plus d’informations, voir [Guide de référence de Java PCKS#11](https://docs.oracle.com/javase/1.5.0/docs/guide/security/p11guide.html).

Pour vérifier que votre fichier de configuration HSM et Sun PKCS#11 sont configurés, saisissez la commande suivante à l’aide de l’outil keytool qui a été installé avec le JDK Java :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Vous avez correctement configuré le HSM si vous pouvez afficher vos informations d’identification dans la liste.

>[!NOTE]
>
>Depuis Java 1.7, Sun Java 64 bits pour Windows ne prend plus en charge les interfaces PKCS#11 requises par Adobe Primetime DRM pour communiquer avec les périphériques HSM. Si vous prévoyez d’utiliser un HSM, veillez à utiliser une version 32 bits de Java ou un JDK prenant en charge les interfaces PKCS#11 complètes.
