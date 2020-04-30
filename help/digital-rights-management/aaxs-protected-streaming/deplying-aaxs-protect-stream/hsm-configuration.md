---
seo-title: Configuration HSM
title: Configuration HSM
uuid: da4d7118-65a8-460d-a796-b7bf5c28b208
translation-type: tm+mt
source-git-commit: ac75f63f98060e1937570476362bb5d4458d1f85

---


# Configuration HSM {#hsm-configuration}

Si vous choisissez d’utiliser un HSM pour stocker les informations d’identification de votre serveur, vous devez charger les clés privées et les certificats sur le HSM et créer un fichier de [!DNL pkcs11.cfg] configuration. Ce fichier doit se trouver dans le répertoire *LicenseServer.ConfigRoot* . Pour obtenir un exemple de fichier de configuration PKCS11, reportez-vous au [!DNL Adobe Access Server for Protected Streaming/configs] répertoire du DVD Adobe Access. Pour plus d’informations sur le format de [!DNL pkcs11.cfg]la bibliothèque, reportez-vous à la documentation du fournisseur Sun PKCS11.

Pour vérifier que votre fichier de configuration HSM et Sun PKCS11 est correctement configuré, vous pouvez utiliser la commande suivante à partir du répertoire où se trouve le [!DNL pkcs11.cfg] fichier ( [!DNL keytool] est installé avec Java JRE et JDK) :

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

Si vos informations d’identification s’affichent dans la liste, le module HSM est correctement configuré et le serveur de licences pourra accéder aux informations d’identification.

>[!NOTE]
>
>Adobe Access Server pour la diffusion en flux continu protégée ne prend actuellement pas en charge les modules HSM sur les systèmes d’exploitation Windows 64 bits.
