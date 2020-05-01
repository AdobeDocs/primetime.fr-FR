---
description: Si vous sélectionnez un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer un fichier de configuration pkcs11.cfg.
seo-description: Si vous sélectionnez un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer un fichier de configuration pkcs11.cfg.
seo-title: Configuration HSM
title: Configuration HSM
uuid: 3610840b-082e-4a73-8aa5-5065f9232e0b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Configuration HSM{#hsm-configuration}

Si vous sélectionnez un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer un fichier de configuration pkcs11.cfg.

Vous devez localiser le fichier de configuration dans le répertoire *LicenseServer.ConfigRoot* .

Pour obtenir un exemple de fichier de configuration PKCS11, reportez-vous au [!DNL Adobe Primetime DRM Server for Protected Streaming/configs] répertoire du DVD DRM d’Adobe Primetime.

Consultez la documentation du fournisseur Sun PKCS11 concernant le format du [!DNL pkcs11.cfg] fichier.

Vous pouvez utiliser la commande suivante à partir du répertoire où se trouve le [!DNL pkcs11.cfg] fichier ( [!DNL keytool] est installé avec Java JRE et JDK) pour vérifier que le fichier de configuration HSM et Sun PKCS11 a été correctement configuré :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Si vous pouvez vue vos informations d’identification dans la liste, le module HSM est correctement configuré et le serveur de licences peut désormais accéder aux informations d’identification.
