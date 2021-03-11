---
title: Obtention des certificats d’autorité de certification de domaine
description: Obtention des certificats d’autorité de certification de domaine
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# Obtention des certificats d&#39;autorité de certification de domaine{#obtain-domain-ca-certificates}

Contrairement au certificat License Server, Packager ou Transport, le certificat d&#39;autorité de certification de domaine n&#39;est pas émis par Adobe. Vous pouvez obtenir ce certificat auprès d’une autorité de certification ou générer un certificat autosigné à utiliser à cette fin.

Le certificat d’autorité de certification de domaine doit utiliser une clé 1024 bits et contenir les attributs standard requis dans un certificat d’autorité de certification :

* Extension de contraintes de base avec l&#39;indicateur CA défini sur true
* Extension d&#39;utilisation de clés indiquant que la signature de certificat est autorisée

Par exemple, avec OpenSSL, un certificat d’autorité de certification auto-signé peut être généré comme suit :

1. Créez un fichier appelé [!DNL ca-extensions.txt] contenant :

   ```
   keyUsage=critical,keyCertSign  
   basicConstraints=critical,CA:TRUE  
   subjectKeyIdentifier=hash 
   ```

1. Générer la clé :

   ```
   openssl genrsa -des3 -out domain-ca.key 1024 
   ```

1. Générer une CSR :

   ```
   openssl req -new -key domain-ca.key -out domain-ca.csr 
   ```

1. Générer un certificat :

   ```
   openssl x509 -req -days 365 -in domain-ca.csr -signkey domain-ca.key \ 
     -out domain-ca.cer -extfile ca-extensions.txt 
   ```

1. Générer un mot de passe :

   ```
   openssl rand -base64 8 
   ```

1. Générer PFX :

   ```
   openssl pkcs12 -export -inkey domain-ca.key \ 
   -in domain-ca.cer -out domain-ca.pfx
   ```

