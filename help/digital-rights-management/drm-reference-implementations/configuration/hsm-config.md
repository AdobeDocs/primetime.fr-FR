---
description: Vous pouvez configurer l’implémentation des références avec le fournisseur Sun PKCS#11 qui prend en charge HSM. Bien que l'utilisation d'un HSM ne soit pas nécessaire, elle est recommandée.
seo-description: Vous pouvez configurer l’implémentation des références avec le fournisseur Sun PKCS#11 qui prend en charge HSM. Bien que l'utilisation d'un HSM ne soit pas nécessaire, elle est recommandée.
seo-title: Configuration HSM
title: Configuration HSM
uuid: 2741ac40-aa42-4aa7-9864-037f3ed3dee2
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# Configuration HSM{#hsm-configuration}

Vous pouvez configurer l’implémentation des références avec le fournisseur Sun PKCS#11 qui prend en charge HSM. Bien que l&#39;utilisation d&#39;un HSM ne soit pas nécessaire, elle est recommandée.

Pour utiliser des informations d’identification sur un HSM, vous devez créer un fichier de configuration pour le fournisseur Sun PKCS#11. Pour plus d&#39;informations, consultez le Guide [de référence](https://docs.oracle.com/javase/1.5.0/docs/guide/security/p11guide.html)Java PCKS#11.

Pour vérifier que votre fichier de configuration HSM et Sun PKCS#11 est configuré, tapez la commande suivante à l’aide de l’outil de commande de clés installé avec le JDK Java :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Vous avez correctement configuré le module HSM si vous pouvez vue vos informations d’identification dans la liste.

>[!NOTE]
>
>Depuis Java 1.7, Sun Java 64 bits pour Windows ne prend plus en charge les interfaces PKCS#11 dont Adobe Primetime DRM a besoin pour communiquer avec les périphériques HSM. Si vous prévoyez d’utiliser un module HSM, veillez à utiliser une version 32 bits de Java ou un JDK prenant en charge les interfaces PKCS#11 complètes.

