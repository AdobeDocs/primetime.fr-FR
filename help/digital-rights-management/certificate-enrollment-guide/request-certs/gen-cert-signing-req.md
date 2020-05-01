---
seo-title: Générer une demande de signature de certificat (demandeur)
title: Générer une demande de signature de certificat (demandeur)
uuid: 04abd5d2-77ac-4f89-8bea-31d389159aee
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# Générer une demande de signature de certificat (demandeur) {#generate-a-certificate-signing-request-requester}

1. Générez une paire de clés. Pour utiliser un utilitaire tel qu’OpenSSL, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl genrsa -des3 -out mycompany-license.key 1024
   ```

   >[!NOTE]
   >
   >Adobe recommande d’inclure le type de certificat (lic, pkgr, trans, trial ou eval) dans le nom de clé. Cette convention d’affectation des noms facilite leur déploiement sur votre serveur de licences. Cet exemple utilise &quot;mycompany-license.key&quot;. Pour les versions d’évaluation et d’évaluation, utilisez &quot;mycompany-eval.key&quot; et &quot;mycompany-trial.key&quot;.

1. Entrez un mot de passe pour protéger la clé privée.

   Les mots de passe doivent contenir au moins 12 caractères. Les caractères doivent inclure un mélange de caractères ASCII majuscules et minuscules et de chiffres. Pour utiliser OpenSSL pour générer un mot de passe fort, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl rand -base64 8
   ```

1. Générer une demande de signature de certificat (CSR).

   Pour utiliser OpenSSL pour générer une CSR, ouvrez une fenêtre de commande et saisissez les informations suivantes :

   ```
   openssl req -new -key mycompany-license.key -out mycompany-license.csr -batch 
   ```

1. Vous êtes invité à saisir le mot de passe de la clé privée.
1. Créez une copie de sauvegarde de votre clé privée et de votre mot de passe.

   Si vous perdez la clé privée ou si elle est compromise, contactez l’administrateur de certificats Adobe pour révoquer votre certificat et en demander un nouveau.

   >[!NOTE]
   >
   >Adobe recommande d’utiliser un HSM pour protéger votre clé privée et votre mot de passe.

