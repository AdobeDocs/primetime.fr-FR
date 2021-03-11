---
title: Création de JKS pour un validateur XSTS
description: Création de JKS pour un validateur XSTS
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 0%

---


# Création de JKS pour un validateur XSTS{#create-jks-for-an-xsts-validator}

1. Recherchez le nom d’alias du certificat privé, situé dans le fichier [!DNL .pfx] partenaire.

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. Convertir [!DNL .pfx] en [!DNL .jks].

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   (où `<alias>` est le nom d’alias du certificat privé que vous avez découvert à l’étape 1.)
1. Importer [!DNL x_secure_token_service.part.xboxlive.com.cer].

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Placez [!DNL xsts.jks] dans votre répertoire d’accueil Tomcat et définissez `-Dxsts-keystore-password=****` pour Tomcat.

Si [!DNL xsts_partner_cert.pfx] et [!DNL xsts.jks] utilisent des mots de passe différents, mettez à jour le mot de passe `xsts` dans `jks` pour qu&#39;ils soient identiques.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
