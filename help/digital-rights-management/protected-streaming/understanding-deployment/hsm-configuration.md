---
description: Si vous sélectionnez un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer un fichier de configuration pkcs11.cfg.
title: Configuration HSM
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# Configuration HSM{#hsm-configuration}

Si vous sélectionnez un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer un fichier de configuration pkcs11.cfg.

Vous devez localiser le fichier de configuration dans le répertoire *LicenseServer.ConfigRoot*.

Pour obtenir un exemple de fichier de configuration PKCS11, consultez le répertoire [!DNL Adobe Primetime DRM Server for Protected Streaming/configs] du DVD DRM Adobe Primetime.

Consultez la documentation du fournisseur Sun PKCS11 concernant le format du fichier [!DNL pkcs11.cfg].

Vous pouvez utiliser la commande suivante à partir du répertoire où se trouve le fichier [!DNL pkcs11.cfg] ( [!DNL keytool] est installé avec Java JRE et JDK) pour vérifier que le fichier de configuration HSM et Sun PKCS11 a été correctement configuré :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Si vous pouvez vue vos informations d’identification dans la liste, le module HSM est correctement configuré et le serveur de licences peut désormais accéder aux informations d’identification.
