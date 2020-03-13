---
description: Vous pouvez configurer l’implémentation des références avec le fournisseur Sun PKCS#11 qui prend en charge HSM. Bien que l’utilisation d’un HSM ne soit pas obligatoire, elle est recommandée.
seo-description: Vous pouvez configurer l’implémentation des références avec le fournisseur Sun PKCS#11 qui prend en charge HSM. Bien que l’utilisation d’un HSM ne soit pas obligatoire, elle est recommandée.
seo-title: Configuration HSM
title: Configuration HSM
uuid: 2741ac40-aa42-4aa7-9864-037f3ed3dee2
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Configuration HSM{#hsm-configuration}

Vous pouvez configurer l’implémentation des références avec le fournisseur Sun PKCS#11 qui prend en charge HSM. Bien que l’utilisation d’un HSM ne soit pas obligatoire, elle est recommandée.

Pour utiliser des informations d’identification sur un HSM, vous devez créer un fichier de configuration pour le fournisseur Sun PKCS#11. Pour plus d&#39;informations, consultez le Guide [de référence](https://docs.oracle.com/javase/1.5.0/docs/guide/security/p11guide.html)Java PCKS#11.

Pour vérifier que votre fichier de configuration HSM et Sun PKCS#11 sont configurés, saisissez la commande suivante à l’aide de l’outil de commande de clés installé avec le JDK Java :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Vous avez correctement configuré le module HSM si vous pouvez  vos informations d’identification dans le .

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Depuis Java 1.7, Sun Java 64 bits pour Windows ne prend plus en charge les interfaces PKCS#11 requises par Adobe Primetime DRM pour communiquer avec les périphériques HSM. Si vous prévoyez d’utiliser un module HSM, veillez à utiliser une version 32 bits de Java ou un JDK prenant en charge les interfaces PKCS#11 complètes.

