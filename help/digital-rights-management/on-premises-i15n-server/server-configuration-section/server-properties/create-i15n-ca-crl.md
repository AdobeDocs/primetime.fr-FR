---
title: Création d’une liste CRL d’autorité de certification d’individualisation
description: Création d’une liste CRL d’autorité de certification d’individualisation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Création d’une liste CRL d’autorité de certification d’individualisation{#create-individualization-ca-crl}

Ce point de distribution Liste de révocation des certificats (CRL) est inclus dans chaque certificat de machine émis par le serveur d’individualisation. Lors de la validation du certificat de la machine sur le serveur de licences, cette CRL sera téléchargée à partir du point de distribution indiqué dans le certificat (ou lue à partir du cache si elle a déjà été téléchargée) et vérifiée pour vérifier que le certificat n’a pas été révoqué.

>[!NOTE]
>
>Pour définir l’URL du point de distribution CRL, vous devez définir la variable [!DNL AdobeInitial.properties] `cert.machine.crldp` champ . Ce point de distribution est *not* vérifié par Primetime DRM pour en connaître la validité. Vous devez vérifier que cette URL est valide. Les erreurs résultant d’une URL non valide ne seront visibles que lorsque les erreurs de validation apparaîtront du serveur de licences.

Les exemples d’instructions présentés ci-dessous sont simplifiés et concernent l’utilisation d’OpenSSL pour créer des listes CRL que votre serveur de licences peut utiliser. Adobe vous recommande d’effectuer ces étapes de manière sécurisée et dans un environnement sécurisé, une fois que des informations d’identification d’autorité de certification de l’individualisation de production ont été obtenues.

1. Modifiez le répertoire de travail en [!DNL create_crl] répertoire inclus dans cette distribution.
1. Copie de votre autorité de certification de l’individualisation [!DNL pfx] à la même [!DNL create_crl] répertoire .

   Les étapes suivantes supposent que la variable Pfx de l’autorité de certification de l’individualisation est nommée [!DNL i15n.pfx]. Ajustez en fonction de votre configuration.
1. Extraire l’autorité de certification de l’individualisation [!DNL pfx] clé privée du fichier.

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

   Cet exemple crée une CRL avec une période de validité d’un mois par défaut. Utilisez la variable `-crldays` et `-crlhours` pour remplacer les valeurs par défaut.

   La génération d’une CRL utilise la variable [!DNL index] et [!DNL crlnumber] pointé vers dans votre [!DNL openssl.conf]. Par défaut, la variable [!DNL demoCA] L’emplacement du répertoire de travail est utilisé. Exemple [!DNL index] et [!DNL crlnumber] Les fichiers sont inclus dans les [!DNL demoCA] répertoire .

1. Déployez le fichier CRL généré à l’étape précédente vers un emplacement approprié accessible par le serveur de licences (par exemple : serveur d’individualisation [!DNL ROOT]).
1. Redémarrez le serveur de licences, une fois la liste de révocation des certificats mise en place.
