---
description: Si vous sélectionnez un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer un fichier de configuration pkcs11.cfg .
title: Configuration HSM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Configuration HSM{#hsm-configuration}

Si vous sélectionnez un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer un fichier de configuration pkcs11.cfg .

Vous devez localiser le fichier de configuration dans la balise *LicenseServer.ConfigRoot* répertoire .

Voir [!DNL Adobe Primetime DRM Server for Protected Streaming/configs] sur le DVD DRM Adobe Primetime pour obtenir un exemple de fichier de configuration PKCS11.

Consultez la documentation du fournisseur Sun PKCS11 concernant le format de [!DNL pkcs11.cfg] fichier .

Vous pouvez utiliser la commande suivante à partir du répertoire où la fonction [!DNL pkcs11.cfg] Le fichier se trouve ( [!DNL keytool] est installé avec Java JRE et JDK) pour vérifier que le fichier de configuration HSM et Sun PKCS11 a été correctement configuré :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Si vous pouvez afficher vos informations d’identification dans la liste, le module HSM est correctement configuré et le serveur de licences peut désormais accéder aux informations d’identification.
