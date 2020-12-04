---
seo-title: Créer une liste CRL d’autorité de certification d’individualisation
title: Créer une liste CRL d’autorité de certification d’individualisation
uuid: f722f3d1-517f-43e3-b892-f9287527fbe6
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Créer une liste CRL d’autorité de certification d’individualisation{#create-individualization-ca-crl}

Ce point de distribution CRL (Certificate Revocation Liste) est inclus dans chaque certificat d&#39;ordinateur émis par le serveur d&#39;individualisation. Lors de la validation du certificat de l’ordinateur sur le serveur de licences, cette liste de révocation des certificats est téléchargée à partir du point de distribution indiqué dans le certificat (ou lue à partir du cache si le certificat a déjà été téléchargé) et vérifiée pour s’assurer que le certificat n’a pas été révoqué.

>[!NOTE]
>
>Pour définir l’URL du point de distribution CRL, vous devez définir le champ [!DNL AdobeInitial.properties] `cert.machine.crldp`. Ce point de distribution est *non* vérifié par Primetime DRM pour vérifier sa validité. Vous devez vérifier que cette URL est valide. Les erreurs résultant d’une URL non valide ne seront pas apparentes tant que les erreurs de validation ne seront pas affichées à partir du serveur de licences.

Les exemples d’instructions fournis ci-dessous sont simplifiés et permettent d’utiliser OpenSSL pour créer des listes CRL que votre serveur de licences peut utiliser. Adobe vous conseille d’effectuer ces étapes de manière sécurisée et avec un environnement, une fois qu’un jeu d’informations d’identification d’autorité de certification d’individualisation de la production a été obtenu.

1. Remplacez le répertoire de travail par le répertoire [!DNL create_crl] inclus dans cette distribution.
1. Copiez votre autorité de certification d’individualisation [!DNL pfx] dans le même répertoire [!DNL create_crl].

   Les étapes suivantes supposent que la variable d’autorité de certification d’individualisation est nommée [!DNL i15n.pfx]. Effectuez les ajustements appropriés à votre configuration.
1. Extrayez la clé privée du fichier d’autorité de certification d’individualisation [!DNL pfx].

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. Convertissez la clé privée au format [!DNL pksc8].

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. Générez la liste CRL.

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   Cet exemple crée une liste CRL avec une période de validité de 1 mois par défaut. Utilisez les options `-crldays` et `-crlhours` pour remplacer les valeurs par défaut.

   La génération d&#39;une liste CRL utilise les fichiers [!DNL index] et [!DNL crlnumber] pointés dans votre [!DNL openssl.conf]. Par défaut, l&#39;emplacement [!DNL demoCA] du répertoire de travail est utilisé. Les exemples de fichiers [!DNL index] et [!DNL crlnumber] sont inclus dans le répertoire [!DNL demoCA] fourni.

1. Déployez le fichier CRL généré à l’étape précédente vers un emplacement approprié accessible par le serveur de licences (par exemple : individualization server [!DNL ROOT]).
1. Redémarrez le serveur de licences une fois que la liste de révocation des certificats est en place.
