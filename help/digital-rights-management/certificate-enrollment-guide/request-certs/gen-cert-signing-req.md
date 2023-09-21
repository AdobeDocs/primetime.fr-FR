---
title: Génération d’une demande de signature de certificat (demandeur)
description: Génération d’une demande de signature de certificat (demandeur)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Génération d’une demande de signature de certificat (demandeur) {#generate-a-certificate-signing-request-requester}

1. Générez une paire de clés. Pour utiliser un utilitaire tel qu’OpenSSL, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl genrsa -des3 -out mycompany-license.key 1024
   ```

   >[!NOTE]
   >
   >Adobe recommande d’inclure le type de certificat (lic, pkgr, trans, try ou eval) dans le nom de la clé. Cette convention d’affectation des noms facilite leur déploiement sur votre serveur de licences. Cet exemple utilise &quot;mycompany-license.key&quot;. Pour les versions d’évaluation et d’évaluation, utilisez &quot;mycompany-eval.key&quot; et &quot;mycompany-Trial.key&quot;.

1. Saisissez un mot de passe pour protéger la clé privée.

   Les mots de passe doivent contenir au moins 12 caractères. Les caractères doivent inclure un mélange de caractères ASCII majuscules et minuscules et de nombres. Pour utiliser OpenSSL pour générer un mot de passe sécurisé, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl rand -base64 8
   ```

1. Générer une demande de signature de certificat (CSR).

   Pour utiliser OpenSSL pour générer une demande de signature de certificat, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl req -new -key mycompany-license.key -out mycompany-license.csr -batch 
   ```

1. Vous êtes invité à saisir le mot de passe de la clé privée.
1. Créez une copie de sauvegarde de votre clé privée et de votre mot de passe.

   Si vous perdez la clé privée ou si elle est compromise, contactez l’administrateur de certificat de l’Adobe pour révoquer votre certificat et en demander un nouveau.

   >[!NOTE]
   >
   >Adobe recommande d’utiliser un HSM pour protéger votre clé privée et votre mot de passe.
