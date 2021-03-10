---
title: Configuration HSM
description: Configuration HSM
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# Configuration HSM {#hsm-configuration}

Si vous choisissez d’utiliser un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer un fichier de configuration [!DNL pkcs11.cfg]. Ce fichier doit se trouver dans le répertoire *LicenseServer.ConfigRoot*. Pour obtenir un exemple de fichier de configuration PKCS11, consultez le répertoire [!DNL Adobe Access Server for Protected Streaming/configs] du DVD d’accès à l’Adobe. Pour plus d&#39;informations sur le format de [!DNL pkcs11.cfg], consultez la documentation du fournisseur Sun PKCS11.

Pour vérifier que votre fichier de configuration HSM et Sun PKCS11 est correctement configuré, vous pouvez utiliser la commande suivante à partir du répertoire où se trouve le fichier [!DNL pkcs11.cfg] ( [!DNL keytool] est installé avec Java JRE et JDK) :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Si vos informations d’identification s’affichent dans la liste, le module HSM est correctement configuré et le serveur de licences pourra accéder aux informations d’identification.

>[!NOTE]
>
>Le serveur d’accès aux Adobes pour la diffusion en flux continu protégée ne prend actuellement pas en charge les modules HSM sur les systèmes d’exploitation Windows 64 bits.
