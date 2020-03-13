---
seo-title: Création de JKS pour un validateur XSTS
title: Création de JKS pour un validateur XSTS
uuid: e02b517d-0b72-4e95-92b2-09b8f785cce6
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Création de JKS pour un validateur XSTS{#create-jks-for-an-xsts-validator}

1. Découvrez le nom d’alias du certificat privé, situé dans le fichier du partenaire [!DNL .pfx] .

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

1. Placez [!DNL xsts.jks] dans votre répertoire d’accueil Tomcat, puis définissez `-Dxsts-keystore-password=****` Tomcat.

Si [!DNL xsts_partner_cert.pfx] et [!DNL xsts.jks] utilisent des mots de passe différents, mettez à jour le `xsts` mot de passe dans `jks` pour qu’ils soient identiques.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
