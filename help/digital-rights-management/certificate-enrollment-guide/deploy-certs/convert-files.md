---
title: Conversion de fichiers
description: Conversion de fichiers
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# Convertir les fichiers{#convert-files}

En utilisant un utilitaire tel qu’OpenSSL et la clé privée, le demandeur génère les fichiers PKCS#12 (pfx) et PEM/DER en saisissant les commandes suivantes à partir d’une fenêtre de commande :

1. Convertissez le fichier PKCS#7 en fichier PEM temporaire.

   Pour utiliser OpenSSL, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl pkcs7 -in mycompany-license.p7b -inform DER -out mycompany-license-temp.pem \ 
   -outform PEM -print_certs 
   ```

   >[!NOTE]
   >
   >Ce PEM temporaire contient votre certificat et les certificats des autorités de certification intermédiaires. Utilisez ces certificats pour générer le fichier PFX.

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
   >Bien que non requis, l’Adobe recommande d’utiliser des mots de passe différents pour la clé privée (private_key_password) et le PFX (pfx_password).

   Ce fichier PEM final contient uniquement votre certificat.

1. Convertissez le fichier PEM en fichier DER.

   Pour utiliser OpenSSL, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl x509 -in mycompany-license.pem -inform PEM -out mycompany-license.der -outform DER 
   ```

   >[!NOTE]
   >
   >Les fichiers DER ne sont requis que pour HTTP Dynamic Streaming packager.

