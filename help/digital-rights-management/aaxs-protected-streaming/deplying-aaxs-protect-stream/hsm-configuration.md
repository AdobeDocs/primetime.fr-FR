---
title: Configuration HSM
description: Configuration HSM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Configuration HSM {#hsm-configuration}

Si vous choisissez d’utiliser un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer une [!DNL pkcs11.cfg] fichier de configuration. Ce fichier doit se trouver dans la variable *LicenseServer.ConfigRoot* répertoire . Voir [!DNL Adobe Access Server for Protected Streaming/configs] sur le DVD Adobe Access pour obtenir un exemple de fichier de configuration PKCS11. Pour plus d’informations sur le format de [!DNL pkcs11.cfg], consultez la documentation du fournisseur Sun PKCS11 .

Pour vérifier que votre fichier de configuration HSM et Sun PKCS11 est correctement configuré, vous pouvez utiliser la commande suivante à partir du répertoire où la variable [!DNL pkcs11.cfg] Le fichier se trouve ( [!DNL keytool] est installé avec Java JRE et JDK) :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Si vos informations d’identification s’affichent dans la liste, le module HSM est correctement configuré et le serveur de licences peut accéder aux informations d’identification.

>[!NOTE]
>
>Le serveur d’accès Adobe pour la diffusion en continu protégée ne prend actuellement pas en charge les modules HSM sur les systèmes d’exploitation Windows 64 bits.
