---
title: Gestion des mises à jour de certificat lors de l’expiration des certificats émis par un Adobe
description: Gestion des mises à jour de certificat lors de l’expiration des certificats émis par un Adobe
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Gestion des mises à jour de certificat lors de l’expiration des certificats émis par un Adobe{#handling-certificate-updates-when-adobe-issued-certificates-expire}

Vous devrez peut-être obtenir un nouveau certificat auprès d’Adobe. Par exemple, un certificat de production expire lorsqu’un certificat d’évaluation expire ou lorsque vous passez d’une évaluation à un certificat de production. Chaque fois qu’un certificat expire et que vous ne souhaitez pas recompresser le contenu qui utilise l’ancien certificat, vous pouvez faire en sorte que le serveur de licences prenne en compte les anciens et les nouveaux certificats.

Pour mettre à jour un serveur avec de nouveaux certificats :

1. (Facultatif) Lorsque vous ajoutez de nouvelles entrées à une liste de mise à jour de stratégie DRM existante ou à une liste de révocation, vous devez signer avec les nouvelles informations d’identification et utiliser l’ancien certificat pour valider la signature sur le fichier existant.

   Par exemple, vous pouvez utiliser la ligne de commande suivante pour ajouter une entrée à une liste de mise à jour de stratégie DRM existante, qui a été signée à l’aide d’informations d’identification différentes :

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. (Facultatif) Utilisez l’API Java pour mettre à jour le serveur de licences avec la nouvelle liste de mise à jour de stratégie DRM ou liste de révocation :

   ```
   HandlerConfiguration.setRevocationList() 
   ```

   ou :

   ```
   HandlerConfiguration.setPolicyUpdateList()
   ```

   Dans l’implémentation de référence, les propriétés que vous utilisez sont `HandlerConfiguration.RevocationList` et `HandlerConfiguration.PolicyUpdateList`. Vous devez également mettre à jour le certificat utilisé pour vérifier les signatures : `RevocationList.verifySignature.X509Certificate`.

1. Mettez à jour le serveur de licences avec les nouveaux et les anciens certificats.

   Si vous souhaitez utiliser du contenu qui a été compilé à l’aide des anciens certificats, assurez-vous que le serveur de licences a accès aux anciennes et nouvelles informations d’identification du serveur de licences, ainsi qu’aux informations d’identification du transport.

   Pour les informations d’identification du serveur de licences :

   * Assurez-vous que les informations d’identification actuelles sont transmises à la variable `LicenseHandler` constructeur :

      * Dans l’implémentation de référence, définissez-la avec la propriété `LicenseHandler.ServerCredential` .
      * Dans Adobe Primetime DRM Server for Protected Streaming, les informations d’identification actuelles doivent être les premières à être spécifiées dans la variable `LicenseServerCredential` dans le fichier flashaccess-tenant.xml .

   * Assurez-vous que les anciennes et actuelles informations d’identification sont fournies à `AsymmetricKeyRetrieval`

      * Dans l’implémentation de référence, définissez-la avec la propriété `LicenseHandler.ServerCredential` et `AsymmetricKeyRetrieval.ServerCredential. n` propriétés.

      * Dans Primetime DRM Server for Protected Streaming, les anciennes informations d’identification sont spécifiées après les premières informations d’identification dans la variable `LicenseServerCredential` dans le fichier flashaccess-tenant.xml .

   Pour les informations d’identification du transport :

   * Assurez-vous que les informations d’identification actuelles sont transmises à la variable `HandlerConfiguration.setServerTransportCredential()` method :

      * Dans l’implémentation de référence, définissez-la avec la propriété `HandlerConfiguration.ServerTransportCredential` .
      * Dans Primetime DRM Server pour la diffusion en continu protégée, les informations d’identification actuelles doivent être les premières à être spécifiées dans la variable `TransportCredential` dans le [!DNL flashaccess-tenant.xml] fichier .

   * Assurez-vous que les anciennes informations d’identification sont fournies à `HandlerConfiguration.setAdditionalServerTransportCredentials`() :

      * Dans l’implémentation de référence, définissez-la avec la propriété `HandlerConfiguration.AdditionalServerTransportCredential. n` propriétés.
      * Dans le serveur DRM Primetime pour la diffusion en continu protégée, il est spécifié après les premières informations d’identification dans la variable `TransportCredential` dans le fichier flashaccess-tenant.xml .

1. Mettez à jour les outils de conditionnement pour vous assurer qu’ils mettent en package le contenu avec les informations d’identification actuelles. Assurez-vous que le dernier certificat du serveur de licences, le certificat de transport et les informations d’identification de packager sont utilisés pour le package.
1. Mettez à jour le certificat du serveur de licences du serveur de clés comme suit :

   * Mettez à jour les informations d’identification dans le fichier de configuration du client de serveur de clés Adobe Primetime DRM en incluant les anciennes et nouvelles informations d’identification du serveur de clés dans flashaccess-keyserver-tenant.xml.
   * Assurez-vous que le certificat actuel est transmis à la variable `HandlerConfiguration.setKeyServerCertificate()` .

      * Dans l’implémentation de référence, définissez-la avec la propriété `HandlerConfiguration.KeyServerCertificate` .
      * Dans Primetime DRM Server for Protected Streaming, spécifiez le certificat du serveur de clés dans le via l’élément Configuration/Tenant/Certificates/KeyServer .
