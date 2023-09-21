---
title: Conversion de fichiers
description: Conversion de fichiers
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Conversion de fichiers{#convert-files}

En utilisant un utilitaire tel qu’OpenSSL et la clé privée, le demandeur génère les fichiers PKCS#12 (pfx) et PEM/DER en saisissant les commandes suivantes à partir d’une fenêtre de commande :

1. Convertissez le fichier PKCS#7 en fichier PEM temporaire.

   Pour utiliser OpenSSL, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl pkcs7 -in mycompany-license.p7b -inform DER -out mycompany-license-temp.pem \ 
   -outform PEM -print_certs 
   ```

   >[!NOTE]
   >
   >Ce modèle PEM temporaire contient votre certificat et les certificats des autorités de certification intermédiaires. Utilisez ces certificats pour générer le fichier PFX.

1. Convertissez le fichier PEM temporaire en fichier PFX.

   Pour utiliser OpenSSL, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl pkcs12 -export -inkey mycompany-license.key -in mycompany-license-temp.pem \ 
   -out mycompany-license.pfx -passin pass:private_key_password -passout pass:pfx_password 
   ```

1. Convertissez le fichier PEM temporaire en fichier PEM final.

   Pour utiliser OpenSSL, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl x509 -in mycompany-license-temp.pem -inform PEM -out mycompany-license.pem -outform PEM 
   ```

   >[!NOTE]
   >
   >Bien que cela ne soit pas obligatoire, Adobe recommande d’utiliser des mots de passe différents pour la clé privée (private_key_password) et le PFX (pfx_password).

   Ce fichier PEM final contient uniquement votre certificat.

1. Convertissez le fichier PEM en fichier DER.

   Pour utiliser OpenSSL, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl x509 -in mycompany-license.pem -inform PEM -out mycompany-license.der -outform DER 
   ```

   >[!NOTE]
   >
   >Les fichiers DER sont requis uniquement pour le HTTP Dynamic Streaming packager.
