---
title: Gestion des mises à jour de certificat lorsque les certificats émis par l’Adobe expirent
description: Gestion des mises à jour de certificat lorsque les certificats émis par l’Adobe expirent
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# Gestion des mises à jour de certificat lorsque les certificats émis par l’Adobe expirent {#handling-certificate-updates-when-your-adobe-issued-certifcates-expire}

Il peut arriver que vous deviez obtenir un nouveau certificat d’Adobe. Par exemple, lorsqu’un certificat de production expire, un certificat d’évaluation expire ou lorsque vous passez d’une évaluation à un certificat de production. Lorsqu’un certificat expire et que vous ne souhaitez pas recompresser le contenu qui utilisait l’ancien certificat. Vous pouvez informer le serveur de licences des anciens et des nouveaux certificats.

Procédez comme suit pour mettre à jour votre serveur avec les nouveaux certificats :

1. (Facultatif) Lors de l’ajout de nouvelles entrées à une liste de mise à jour de stratégie ou de révocation existante, veillez à signer avec les nouvelles informations d’identification et utilisez l’ancien certificat pour valider la signature sur le fichier existant.

   Par exemple, utilisez la ligne de commande suivante pour ajouter une entrée à une liste de mise à jour de stratégie existante, qui a été signée à l’aide d’informations d’identification différentes :

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. Utilisez l’API Java pour mettre à jour le serveur de licences avec la nouvelle liste de mise à jour de stratégie ou liste de révocation :

   ```
    HandlerConfiguration.setRevocationList() 
   ```

   ou :

   ```
    HandlerConfiguration.setPolicyUpdateList()
   ```

   Dans l’implémentation de référence, les propriétés que vous utilisez sont `HandlerConfiguration.RevocationList` et `HandlerConfiguration.PolicyUpdateList`. Mettez également à jour le certificat utilisé pour vérifier les signatures : `RevocationList.verifySignature.X509Certificate`.

1. Pour utiliser du contenu qui était compilé à l’aide des anciens certificats, le serveur de licences requiert les anciennes et nouvelles informations d’identification du serveur de licences et les informations d’identification du transport. Mettez à jour le serveur de licences avec les nouveaux et les anciens certificats.

   Pour les informations d’identification du serveur de licences :

   * Assurez-vous que les informations d’identification actuelles sont transmises à la variable `LicenseHandler` constructeur :

      * Dans l’implémentation de référence, définissez-la via le `LicenseHandler.ServerCredential` .
      * Dans Adobe Access Server for Protected Streaming, les informations d’identification actuelles doivent être les premières à être spécifiées dans la variable `LicenseServerCredential` dans le fichier flashaccess-tenant.xml .

   * Assurez-vous que les anciennes et actuelles informations d’identification sont fournies à `AsymmetricKeyRetrieval`

      * Dans l’implémentation de référence, définissez-la via le `LicenseHandler.ServerCredential` et `AsymmetricKeyRetrieval.ServerCredential. n` propriétés.
      * Dans Adobe Access Server for Protected Streaming, les anciennes informations d’identification sont spécifiées après les premières informations d’identification dans la variable `LicenseServerCredential` dans le fichier flashaccess-tenant.xml .

   Pour les informations d’identification du transport :

   * Assurez-vous que les informations d’identification actuelles sont transmises à la variable `HandlerConfiguration.setServerTransportCredential()` method :

      * Dans l’implémentation de référence, définissez-la via le `HandlerConfiguration.ServerTransportCredential` .
      * Dans Adobe Access Server pour la diffusion en continu protégée, les informations d’identification actuelles doivent être les premières spécifiées dans la variable `TransportCredential` dans le fichier flashaccess-tenant.xml .

   * Assurez-vous que les anciennes informations d’identification sont fournies à `HandlerConfiguration.setAdditionalServerTransportCredentials`() :

      * Dans l’implémentation de référence, définissez-la via le `HandlerConfiguration.AdditionalServerTransportCredential. n` propriétés.
      * Dans Adobe Access Server pour la diffusion en continu protégée, elle est spécifiée après les premières informations d’identification dans la variable `TransportCredential` dans le fichier flashaccess-tenant.xml .

1. Mettez à jour les outils de conditionnement pour vous assurer qu’ils regroupent le contenu avec les informations d’identification actuelles. Assurez-vous que le dernier certificat du serveur de licences, le certificat de transport et les informations d’identification de packager sont utilisés pour le package.
1. Pour mettre à jour le certificat du serveur de licences du serveur de clés :

   * Mettez à jour les informations d’identification dans le fichier de configuration du client Adobe Access Key Server. Incluez les anciennes et nouvelles informations d’identification du serveur de clés dans flashaccess-keyserver-tenant.xml.
   * Assurez-vous que le certificat actuel est transmis à la variable `HandlerConfiguration.setKeyServerCertificate()` .

      * Dans l’implémentation de référence, définissez-la via le `HandlerConfiguration.KeyServerCertificate` .
      * Dans Adobe Access Server for Protected Streaming, spécifiez le certificat du serveur de clés dans via l’élément Configuration/Tenant/Certificates/KeyServer .
