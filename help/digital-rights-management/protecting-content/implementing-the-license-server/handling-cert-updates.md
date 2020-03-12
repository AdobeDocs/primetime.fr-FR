---
seo-title: Gestion des mises à jour de certificat à l’expiration des certificats émis par Adobe
title: Gestion des mises à jour de certificat à l’expiration des certificats émis par Adobe
uuid: abc0ca3e-a78f-4078-9480-7116843cce05
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gestion des mises à jour de certificat à l’expiration des certificats émis par Adobe{#handling-certificate-updates-when-adobe-issued-certificates-expire}

Vous devrez peut-être obtenir un nouveau certificat auprès d’Adobe. Par exemple, un certificat de production expire lorsqu’un certificat d’évaluation expire ou lorsque vous passez d’une évaluation à un certificat de production. Chaque fois qu’un certificat expire et que vous ne souhaitez pas recompresser le contenu qui utilise l’ancien certificat, vous pouvez rendre le serveur de licences conscient à la fois des anciens et des nouveaux certificats.

Pour mettre à jour un serveur avec de nouveaux certificats :

1. (Facultatif) Lorsque vous ajoutez de nouvelles entrées à un de mise à jour de stratégie DRM ou à un de révocation existant, vous devez vous connecter avec les nouvelles informations d’identification et utiliser l’ancien certificat pour valider la signature sur le fichier existant.

   Par exemple, vous pouvez utiliser la ligne de commande suivante pour ajouter une entrée à un de mise à jour de stratégie DRM existant, qui a été signé à l’aide d’informations d’identification différentes :

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. (Facultatif) Utilisez l’API Java pour mettre à jour le serveur de licences avec le nouveau de mise à jour de stratégie DRM ou le nouveau de révocation  :

   ```
   HandlerConfiguration.setRevocationList() 
   ```

   ou :

   ```
   HandlerConfiguration.setPolicyUpdateList()
   ```

   Dans l’implémentation de référence, les propriétés que vous utilisez sont `HandlerConfiguration.RevocationList` et `HandlerConfiguration.PolicyUpdateList`. Vous devez également mettre à jour le certificat utilisé pour vérifier les signatures : `RevocationList.verifySignature.X509Certificate`.

1. Mettez à jour le serveur de licences avec les nouveaux et les anciens certificats.

   Si vous souhaitez consommer du contenu qui a été compressé à l’aide des anciens certificats, assurez-vous que le serveur de licences a accès aux anciennes et nouvelles informations d’identification du serveur de licences, ainsi qu’aux informations d’identification de transport.

   Pour les informations d’identification du serveur de licences :

   * Assurez-vous que les informations d’identification actuelles sont transmises au `LicenseHandler` constructeur :

      * Dans l’implémentation de référence, définissez-la avec la `LicenseHandler.ServerCredential` propriété.
      * Dans Adobe Primetime DRM Server for Protected Streaming, les informations d’identification actuelles doivent être les premières à être spécifiées dans l’ `LicenseServerCredential` élément du fichier flashaccess-tenant.xml.
   * Vérifiez que les informations d’identification actuelles et anciennes sont fournies à la section `AsymmetricKeyRetrieval`

      * Dans l’implémentation de référence, définissez-la avec les propriétés `LicenseHandler.ServerCredential` et `AsymmetricKeyRetrieval.ServerCredential. n` .

      * Dans le serveur DRM Primetime pour la diffusion en flux continu protégée, les anciennes informations d’identification sont spécifiées après les premières informations d’identification dans l’ `LicenseServerCredential` élément du fichier flashaccess-tenant.xml.
   Pour les informations d’identification de transport :

   * Vérifiez que les informations d’identification actuelles sont transmises à la `HandlerConfiguration.setServerTransportCredential()` méthode :

      * Dans l’implémentation de référence, définissez-la avec la `HandlerConfiguration.ServerTransportCredential` propriété.
      * Dans le serveur DRM Primetime pour la diffusion protégée, les informations d’identification actuelles doivent être les premières à être spécifiées dans l’ `TransportCredential` élément du [!DNL flashaccess-tenant.xml] fichier.
   * Vérifiez que les anciennes informations d’identification sont fournies à `HandlerConfiguration.setAdditionalServerTransportCredentials`() :

      * Dans l’implémentation de référence, définissez-la avec les `HandlerConfiguration.AdditionalServerTransportCredential. n` propriétés.
      * Dans le serveur DRM Primetime pour la diffusion protégée, cette valeur est spécifiée après les premières informations d’identification dans l’ `TransportCredential` élément du fichier flashaccess-tenant.xml.




1. Mettez à jour les outils de création de package pour vous assurer qu’ils compressent le contenu avec les informations d’identification actuelles. Assurez-vous que le certificat du serveur de licences, le certificat de transport et les informations d’identification du gestionnaire de package les plus récents sont utilisés pour le pack.
1. Mettez à jour le certificat du serveur de licences du serveur de clés comme suit :

   * Mettez à jour les informations d’identification dans le fichier de configuration du client Adobe Primetime DRM Key Server en incluant les anciennes et les nouvelles informations d’identification de Key Server dans flashaccess-keyserver-tenant.xml.
   * Assurez-vous que le certificat actuel est transmis à la `HandlerConfiguration.setKeyServerCertificate()` méthode.

      * Dans l’implémentation de référence, définissez-la avec la `HandlerConfiguration.KeyServerCertificate` propriété.
      * Dans le serveur DRM Primetime pour la diffusion en flux continu protégée, spécifiez le certificat du serveur de clés dans l’élément Configuration/Tenant/Certificates/KeyServer.

