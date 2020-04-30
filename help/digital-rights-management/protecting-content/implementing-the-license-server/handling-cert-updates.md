---
seo-title: Gestion des mises à jour des certificats à l’expiration des certificats émis par Adobe
title: Gestion des mises à jour des certificats à l’expiration des certificats émis par Adobe
uuid: abc0ca3e-a78f-4078-9480-7116843cce05
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gestion des mises à jour des certificats à l’expiration des certificats émis par Adobe{#handling-certificate-updates-when-adobe-issued-certificates-expire}

Vous devrez peut-être obtenir un nouveau certificat auprès d’Adobe. Par exemple, un certificat de production expire lorsqu’un certificat d’évaluation expire ou lorsque vous passez d’une évaluation à un certificat de production. Chaque fois qu’un certificat expire et que vous ne souhaitez pas recompresser le contenu qui utilise l’ancien certificat, vous pouvez rendre le serveur de licences conscient à la fois des anciens et des nouveaux certificats.

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

   * Assurez-vous que les informations d’identification actuelles sont transmises au `LicenseHandler` constructeur :

      * Dans l’implémentation de référence, définissez-la avec la `LicenseHandler.ServerCredential` propriété.
      * Dans Adobe Primetime DRM Server for Protected Streaming, les informations d’identification actuelles doivent être les premières à être spécifiées dans l’ `LicenseServerCredential` élément du fichier flashaccess-locataire.xml.
   * Assurez-vous que les informations d’identification actuelles et anciennes sont fournies à `AsymmetricKeyRetrieval`

      * Dans l’implémentation de référence, définissez-la avec les propriétés `LicenseHandler.ServerCredential` et `AsymmetricKeyRetrieval.ServerCredential. n` .

      * Dans Primetime DRM Server for Protected Streaming, les anciennes informations d’identification sont spécifiées après les premières informations d’identification dans l’ `LicenseServerCredential` élément du fichier flashaccess-locataire.xml.
   Pour les informations d&#39;identification de transport :

   * Assurez-vous que les informations d’identification actuelles sont transmises à la `HandlerConfiguration.setServerTransportCredential()` méthode :

      * Dans l’implémentation de référence, définissez-la avec la `HandlerConfiguration.ServerTransportCredential` propriété.
      * Dans le serveur DRM Primetime pour la diffusion en flux continu protégée, les informations d’identification actuelles doivent être les premières à être spécifiées dans l’ `TransportCredential` élément du [!DNL flashaccess-tenant.xml] fichier.
   * Assurez-vous que les anciennes informations d’identification sont fournies à `HandlerConfiguration.setAdditionalServerTransportCredentials`() :

      * Dans l’implémentation de référence, définissez-la avec les `HandlerConfiguration.AdditionalServerTransportCredential. n` propriétés.
      * Dans le serveur DRM Primetime pour la diffusion en flux continu protégée, cette valeur est spécifiée après les premières informations d’identification dans l’ `TransportCredential` élément du fichier flashaccess-locataire.xml.




1. Mettez à jour les outils de création de package pour vous assurer qu’ils emballent le contenu avec les informations d’identification actuelles. Assurez-vous que le dernier certificat de serveur de licences, le certificat de transport et les informations d’identification de packager sont utilisés pour le pack.
1. Mettez à jour le certificat du serveur de licences du serveur de clés comme suit :

   * Mettez à jour les informations d’identification dans le fichier de configuration du client Adobe Primetime DRM Key Server en incluant à la fois les anciennes et les nouvelles informations d’identification Key Server dans flashaccess-keyserver-locataire.xml.
   * Assurez-vous que le certificat actuel est transmis à la `HandlerConfiguration.setKeyServerCertificate()` méthode.

      * Dans l’implémentation de référence, définissez-la avec la `HandlerConfiguration.KeyServerCertificate` propriété.
      * Dans le serveur DRM Primetime pour la diffusion en flux continu protégée, spécifiez le certificat du serveur de clés dans l’élément Configuration/Tenant/Certificates/KeyServer.

