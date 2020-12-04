---
seo-title: Renouveler les certificats
title: Renouveler les certificats
uuid: 12a560b0-966b-424e-bfe5-22e9c10d8667
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---


# Renouveler les certificats {#renew-certificates}

Vous devez connaître les restrictions de renouvellement de certificat suivantes, basées sur votre configuration de SDK DRM Adobe Primetime :

* SDK de production DRM Primetime

   Adobe fournit l’ensemble initial de certificats gratuits pour le SDK de production DRM Primetime lorsque vous achetez un contrat d’assistance. Si vous ne disposez pas d’un contrat d’assistance, vous pouvez acheter un ensemble de certificats de renouvellement valables deux ans.
* SDK d’évaluation DRM Primetime

   Le certificat défini pour ce SDK est valide pendant un an et ne peut pas être renouvelé.
* SDK d’évaluation DRM Primetime

   Le SDK d’évaluation DRM de Primetime est valide pendant trois mois et l’Adobe fournit un ensemble de certificats de renouvellement gratuits.

## Implémentation de nouveaux certificats et utilisation d’anciens certificats pour le contenu existant {#section_345C92D1C9794B0BBB9A9B0702EC95FF}

Dans Primetime DRM, vous pouvez autoriser un serveur de licences à émettre une licence pour le contenu conditionné avec des certificats de Packager antérieurs (ou même expirés). Pour configurer votre serveur afin qu’il accepte les demandes de licence provenant de contenus précédemment assemblés, fournissez votre ancien certificat à votre serveur et mettez à jour le fichier de configuration de votre serveur afin que le serveur sache où trouver les anciens certificats. Pour plus d’informations, voir *Gestion des mises à jour de certificats lorsque les certificats émis par l’Adobe arrivent à expiration* dans *Utilisation du SDK DRM Adobe Primetime pour la protection du contenu*.

Si votre application serveur repose sur l’implémentation de référence DRM de Primetime, vous n’avez pas à mettre à jour votre programme côté serveur. Dans le fichier `flashaccess-refimpl.properties`, il existe des champs dans lesquels vous pouvez spécifier des certificats de transport et de serveur de licences supplémentaires. Si vous n’avez qu’un seul certificat, vous n’avez pas à renseigner ces propriétés. Si vous avez des certificats expirés et souhaitez utiliser ces certificats lorsque vous émettez des réponses de licence, vous devez fournir ces certificats au fichier de configuration et redémarrer votre serveur.

Pour spécifier d’anciens certificats, utilisez les propriétés suivantes :

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`

