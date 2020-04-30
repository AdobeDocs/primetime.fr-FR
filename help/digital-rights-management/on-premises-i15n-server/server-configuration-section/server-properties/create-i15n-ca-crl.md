---
seo-title: Créer une liste CRL d’autorité de certification d’individualisation
title: Créer une liste CRL d’autorité de certification d’individualisation
uuid: f722f3d1-517f-43e3-b892-f9287527fbe6
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Créer une liste CRL d’autorité de certification d’individualisation{#create-individualization-ca-crl}

Ce point de distribution CRL (Certificate Revocation Liste) est inclus dans chaque certificat d&#39;ordinateur émis par le serveur d&#39;individualisation. Lors de la validation du certificat de l’ordinateur sur le serveur de licences, cette liste de révocation des certificats est téléchargée à partir du point de distribution indiqué dans le certificat (ou lue à partir du cache si le certificat a déjà été téléchargé) et vérifiée pour s’assurer que le certificat n’a pas été révoqué.

>[!NOTE]
>
>Pour définir l’URL du point de distribution CRL, vous devez définir le [!DNL AdobeInitial.properties]`cert.machine.crldp` champ. Ce point de distribution *n&#39;est pas* vérifié par Primetime DRM pour vérifier sa validité. Vous devez vérifier que cette URL est valide. Les erreurs résultant d’une URL non valide ne seront pas apparentes tant que les erreurs de validation ne seront pas affichées à partir du serveur de licences.

Les exemples d’instructions fournis ci-dessous sont simplifiés et permettent d’utiliser OpenSSL pour créer des listes CRL que votre serveur de licences peut utiliser. Adobe vous recommande d’effectuer ces étapes de manière sécurisée et avec un environnement, une fois les informations d’identification d’autorité de certification d’individualisation de la production obtenues.

1. Remplacez le répertoire de travail par le [!DNL create_crl] répertoire inclus dans cette distribution.
1. Copiez votre autorité de certification d’individualisation [!DNL pfx] dans le même [!DNL create_crl] répertoire.

   Les étapes suivantes supposent que la variable d’autorité de certification d’individualisation est nommée [!DNL i15n.pfx]. Effectuez les ajustements appropriés à votre configuration.
1. Extrayez la clé privée du [!DNL pfx] fichier d’autorité de certification d’individualisation.

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. Convertir la clé privée en [!DNL pksc8] format.

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. Générez la liste CRL.

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   Cet exemple crée une liste CRL avec une période de validité de 1 mois par défaut. Utilisez les options `-crldays` et `-crlhours` pour remplacer les valeurs par défaut.

   La génération d’une CRL utilise le fichier [!DNL index] et [!DNL crlnumber] pointé dans votre [!DNL openssl.conf]formulaire. Par défaut, l’ [!DNL demoCA] emplacement du répertoire de travail est utilisé. Les exemples [!DNL index] et les [!DNL crlnumber] fichiers sont inclus dans le [!DNL demoCA] répertoire fourni.

1. Déployez le fichier CRL généré à l’étape précédente vers un emplacement approprié accessible par le serveur de licences (par exemple : individualization server [!DNL ROOT]).
1. Redémarrez le serveur de licences une fois la liste de révocation des certificats mise en place.
