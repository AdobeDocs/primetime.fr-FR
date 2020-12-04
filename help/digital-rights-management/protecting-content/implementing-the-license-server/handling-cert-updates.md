---
seo-title: Gestion des mises à jour des certificats à l’expiration des certificats émis par Adobe
title: Gestion des mises à jour des certificats à l’expiration des certificats émis par Adobe
uuid: abc0ca3e-a78f-4078-9480-7116843cce05
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Gestion des mises à jour des certificats lorsque les certificats émis par Adobe arrivent à expiration{#handling-certificate-updates-when-adobe-issued-certificates-expire}

Vous devrez peut-être obtenir un nouveau certificat auprès d&#39;Adobe. Par exemple, un certificat de production expire lorsqu’un certificat d’évaluation expire ou lorsque vous passez d’une évaluation à un certificat de production. Chaque fois qu’un certificat expire et que vous ne souhaitez pas recompresser le contenu qui utilise l’ancien certificat, vous pouvez rendre le serveur de licences conscient à la fois des anciens et des nouveaux certificats.

Pour mettre à jour un serveur avec de nouveaux certificats :

1. (Facultatif) Lorsque vous ajoutez de nouvelles entrées à une liste de mise à jour ou à une liste de révocation de stratégie DRM existante, vous devez vous connecter avec les nouvelles informations d’identification et utiliser l’ancien certificat pour valider la signature sur le fichier existant.

   Par exemple, vous pouvez utiliser la ligne de commande suivante pour ajouter une entrée à une liste de mise à jour de stratégie DRM existante, qui a été signée à l’aide d’informations d’identification différentes :

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. (Facultatif) Utilisez l’API Java pour mettre à jour le serveur de licences avec la nouvelle liste de mise à jour ou liste de révocation de la stratégie DRM :

   ```
   HandlerConfiguration.setRevocationList() 
   ```

   ou :

   ```
   HandlerConfiguration.setPolicyUpdateList()
   ```

   Dans l’implémentation de référence, les propriétés que vous utilisez sont `HandlerConfiguration.RevocationList` et `HandlerConfiguration.PolicyUpdateList`. Vous devez également mettre à jour le certificat utilisé pour vérifier les signatures : `RevocationList.verifySignature.X509Certificate`.

1. Mettez à jour le serveur de licences avec les nouveaux et les anciens certificats.

   Si vous souhaitez consommer du contenu qui a été compilé à l’aide des anciens certificats, assurez-vous que le serveur de licences a accès aux anciennes et nouvelles informations d’identification du serveur de licences ainsi qu’aux informations d’identification de transport.

   Pour les informations d’identification du serveur de licences :

   * Assurez-vous que les informations d’identification actuelles sont transmises au constructeur `LicenseHandler` :

      * Dans l’implémentation de référence, définissez-la avec la propriété `LicenseHandler.ServerCredential`.
      * Dans Adobe Primetime DRM Server for Protected Streaming, les informations d’identification actuelles doivent être les premières à être spécifiées dans l’élément `LicenseServerCredential` du fichier flashaccess-locataire.xml.
   * Vérifier que les informations d’identification actuelles et anciennes sont fournies à `AsymmetricKeyRetrieval`

      * Dans l’implémentation de référence, définissez-la avec les propriétés `LicenseHandler.ServerCredential` et `AsymmetricKeyRetrieval.ServerCredential. n`.

      * Dans Primetime DRM Server for Protected Streaming, les anciennes informations d’identification sont spécifiées après les premières informations d’identification dans l’élément `LicenseServerCredential` du fichier flashaccess-locataire.xml.

   Pour les informations d&#39;identification de transport :

   * Assurez-vous que les informations d’identification actuelles sont transmises à la méthode `HandlerConfiguration.setServerTransportCredential()` :

      * Dans l’implémentation de référence, définissez-la avec la propriété `HandlerConfiguration.ServerTransportCredential`.
      * Dans le serveur DRM Primetime pour la diffusion en flux continu protégée, les informations d’identification actuelles doivent être les premières à être spécifiées dans l’élément `TransportCredential` du fichier [!DNL flashaccess-tenant.xml].
   * Assurez-vous que les anciennes informations d’identification sont fournies à `HandlerConfiguration.setAdditionalServerTransportCredentials`() :

      * Dans l’implémentation de référence, définissez-la avec les propriétés `HandlerConfiguration.AdditionalServerTransportCredential. n`.
      * Dans le serveur DRM Primetime pour la diffusion en flux continu protégée, cette valeur est spécifiée après les premières informations d’identification dans l’élément `TransportCredential` du fichier flashaccess-locataire.xml.




1. Mettez à jour les outils de création de package pour vous assurer qu’ils emballent le contenu avec les informations d’identification actuelles. Assurez-vous que le dernier certificat de serveur de licences, le certificat de transport et les informations d’identification de packager sont utilisés pour le pack.
1. Mettez à jour le certificat du serveur de licences du serveur de clés comme suit :

   * Mettez à jour les informations d’identification dans le fichier de configuration du client du serveur de clés DRM Adobe Primetime en incluant les anciennes et les nouvelles informations d’identification du serveur de clés dans flashaccess-keyserver-tenant.xml.
   * Assurez-vous que le certificat actuel est transmis à la méthode `HandlerConfiguration.setKeyServerCertificate()`.

      * Dans l’implémentation de référence, définissez-la avec la propriété `HandlerConfiguration.KeyServerCertificate`.
      * Dans le serveur DRM Primetime pour la diffusion en flux continu protégée, spécifiez le certificat du serveur de clés dans l’élément Configuration/Tenant/Certificates/KeyServer.

