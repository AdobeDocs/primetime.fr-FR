---
title: Obtention de certificats d’autorité de certification de domaine
description: Obtention de certificats d’autorité de certification de domaine
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Obtention de certificats d’autorité de certification de domaine{#obtain-domain-ca-certificates}

Contrairement au certificat du serveur de licences, de Packager ou de transport, le certificat de l’autorité de certification du domaine n’est pas émis par Adobe. Vous pouvez obtenir ce certificat auprès d’une autorité de certification ou générer un certificat autosigné à utiliser à cette fin.

Le certificat d’autorité de certification du domaine doit utiliser une clé 1 024 bits et contenir les attributs standard requis dans un certificat d’autorité de certification :

* Extension de contraintes de base avec l’indicateur CA défini sur true
* L’extension d’utilisation de clé spécifiant la signature de certificat est autorisée

Par exemple, avec OpenSSL, un certificat d’autorité de certification auto-signé peut être généré comme suit :

1. Créez un fichier appelé [!DNL ca-extensions.txt] contain :

   ```
   keyUsage=critical,keyCertSign  
   basicConstraints=critical,CA:TRUE  
   subjectKeyIdentifier=hash 
   ```

1. Générer la clé :

   ```
   openssl genrsa -des3 -out domain-ca.key 1024 
   ```

1. Générer une demande de signature de certificat :

   ```
   openssl req -new -key domain-ca.key -out domain-ca.csr 
   ```

1. Générer un certificat :

   ```
   openssl x509 -req -days 365 -in domain-ca.csr -signkey domain-ca.key \ 
     -out domain-ca.cer -extfile ca-extensions.txt 
   ```

1. Générer le mot de passe :

   ```
   openssl rand -base64 8 
   ```

1. Generate PFX :

   ```
   openssl pkcs12 -export -inkey domain-ca.key \ 
   -in domain-ca.cer -out domain-ca.pfx
   ```
