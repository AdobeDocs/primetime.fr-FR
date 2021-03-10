---
title: Gestion des mises à jour des certificats lorsque vos certificats émis par Adobe arrivent à expiration
description: Gestion des mises à jour des certificats lorsque vos certificats émis par Adobe arrivent à expiration
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---


# Gestion des mises à jour de certificats lorsque vos certificats émis par Adobe arrivent à expiration {#handling-certificate-updates-when-your-adobe-issued-certifcates-expire}

Il peut arriver que vous deviez obtenir un nouveau certificat de l&#39;Adobe. Par exemple, lorsqu’un certificat de production expire, un certificat d’évaluation expire ou lorsque vous passez d’une évaluation à un certificat de production. Lorsqu’un certificat expire et que vous ne souhaitez pas recompresser le contenu qui utilisait l’ancien certificat. Vous pouvez informer le serveur de licences des anciens et des nouveaux certificats.

Procédez comme suit pour mettre à jour votre serveur avec les nouveaux certificats :

1. (Facultatif) Lorsque vous ajoutez de nouvelles entrées à une liste de mise à jour de stratégie ou à une liste de révocation existante, veillez à vous connecter avec les nouvelles informations d’identification et utilisez l’ancien certificat pour valider la signature sur le fichier existant.

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

1. Pour consommer du contenu qui était compressé à l’aide des anciens certificats, le serveur de licences requiert les anciennes et nouvelles informations d’identification du serveur de licences et les informations d’identification de transport. Mettez à jour le serveur de licences avec les nouveaux et les anciens certificats.

   Pour les informations d’identification du serveur de licences :

   * Assurez-vous que les informations d’identification actuelles sont transmises au constructeur `LicenseHandler` :

      * Dans l’implémentation de référence, définissez-la via la propriété `LicenseHandler.ServerCredential`.
      * Dans Adobe Access Server for Protected Streaming, les informations d’identification actuelles doivent être les premières à être spécifiées dans l’élément `LicenseServerCredential` du fichier flashaccess-locataire.xml.
   * Vérifier que les informations d’identification actuelles et anciennes sont fournies à `AsymmetricKeyRetrieval`

      * Dans l’implémentation de référence, définissez-la via les propriétés `LicenseHandler.ServerCredential` et `AsymmetricKeyRetrieval.ServerCredential. n`.
      * Dans Adobe Access Server for Protected Streaming, les anciennes informations d’identification sont spécifiées après les premières informations d’identification dans l’élément `LicenseServerCredential` du fichier flashaccess-locataire.xml.

   Pour les informations d&#39;identification de transport :

   * Assurez-vous que les informations d’identification actuelles sont transmises à la méthode `HandlerConfiguration.setServerTransportCredential()` :

      * Dans l’implémentation de référence, définissez-la via la propriété `HandlerConfiguration.ServerTransportCredential`.
      * Dans l’Adobe Access Server pour la diffusion en flux continu protégée, les informations d’identification actuelles doivent être les premières à être spécifiées dans l’élément `TransportCredential` du fichier flashaccess-locataire.xml.
   * Assurez-vous que les anciennes informations d’identification sont fournies à `HandlerConfiguration.setAdditionalServerTransportCredentials`() :

      * Dans l’implémentation de référence, définissez-la via les propriétés `HandlerConfiguration.AdditionalServerTransportCredential. n`.
      * Dans l’Adobe Access Server pour la diffusion en flux continu protégée, cette valeur est spécifiée après les premières informations d’identification dans l’élément `TransportCredential` du fichier flashaccess-locataire.xml.




1. Mettez à jour les outils de création de package pour vous assurer qu’ils emballent le contenu avec les informations d’identification actuelles. Assurez-vous que le dernier certificat de serveur de licences, le certificat de transport et les informations d’identification de packager sont utilisés pour le pack.
1. Pour mettre à jour le certificat du serveur de licences du serveur de clés :

   * Mettez à jour les informations d&#39;identification dans le fichier de configuration du client Adobe Access Key Server. Incluez les anciennes et les nouvelles informations d’identification du serveur de clés dans flashaccess-keyserver-locataire.xml.
   * Assurez-vous que le certificat actuel est transmis à la méthode `HandlerConfiguration.setKeyServerCertificate()`.

      * Dans l’implémentation de référence, définissez-la via la propriété `HandlerConfiguration.KeyServerCertificate`.
      * Dans l’Adobe Access Server for Protected Streaming, spécifiez le certificat du serveur de clés dans l’élément Configuration/Tenant/Certificates/KeyServer.

