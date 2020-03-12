---
seo-title: Obtention des certificats d'autorité de certification de domaine
title: Obtention des certificats d'autorité de certification de domaine
uuid: 41bbe02b-363a-47f4-9cc0-350730b6c787
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# Obtention des certificats d&#39;autorité de certification de domaine{#obtain-domain-ca-certificates}

Contrairement au certificat License Server, Packager ou Transport, le certificat d’autorité de certification de domaine n’est pas émis par Adobe. Vous pouvez obtenir ce certificat auprès d’une autorité de certification ou générer un certificat autosigné à utiliser à cette fin.

Le certificat d’autorité de certification de domaine doit utiliser une clé 1024 bits et contenir les attributs standard requis dans un certificat d’autorité de certification :

* Extension Contraintes de base avec l&#39;indicateur CA défini sur true
* Extension d’utilisation de clé spécifiant la signature de certificat autorisée

Par exemple, avec OpenSSL, un certificat d’autorité de certification autosigné peut être généré comme suit :

1. Créez un fichier nommé [!DNL ca-extensions.txt] contenant :

   ```
   keyUsage=critical,keyCertSign  
   basicConstraints=critical,CA:TRUE  
   subjectKeyIdentifier=hash 
   ```

1. Générer la clé :

   ```
   openssl genrsa -des3 -out domain-ca.key 1024 
   ```

1. Générer un fichier CSR :

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

1. Générer le fichier PFX :

   ```
   openssl pkcs12 -export -inkey domain-ca.key \ 
   -in domain-ca.cer -out domain-ca.pfx
   ```

