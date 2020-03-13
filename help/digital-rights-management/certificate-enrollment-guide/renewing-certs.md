---
seo-title: Renouveler les certificats
title: Renouveler les certificats
uuid: 12a560b0-966b-424e-bfe5-22e9c10d8667
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# Renouveler les certificats{#renew-certificates}

Vous devez connaître les restrictions de renouvellement de certificat suivantes, basées sur votre configuration du SDK DRM d’Adobe Primetime :

* SDK de production DRM Primetime

   Adobe fournit l’ensemble initial de certificats gratuits pour le SDK de production DRM Primetime lorsque vous achetez un contrat d’assistance. Si vous ne disposez pas d’un contrat d’assistance, vous pouvez acheter un ensemble de certificats de renouvellement valides pendant deux ans.
* SDK d’évaluation DRM Primetime

   Le jeu de certificats pour ce SDK est valide pendant un an et ne peut pas être renouvelé.
* SDK d’évaluation DRM Primetime

   Le SDK d’évaluation DRM de Primetime est valide pendant trois mois et Adobe fournit un ensemble de certificats de renouvellement gratuits.

## Implémentation de nouveaux certificats et utilisation d’anciens certificats pour le contenu existant {#section_345C92D1C9794B0BBB9A9B0702EC95FF}

Dans le DRM Primetime, vous pouvez autoriser un serveur de licences à émettre une licence pour le contenu fourni avec des certificats de mise en package antérieurs (voire expirés). Pour configurer votre serveur afin qu’il accepte les demandes de licence issues de contenus précédemment assemblés, fournissez votre ancien certificat à votre serveur et mettez à jour le fichier de configuration de votre serveur afin que le serveur sache où trouver les anciens certificats. Pour plus d’informations, voir *Gestion des mises à jour de certificat lorsque les certificats émis par Adobe expirent* dans *Utilisation du SDK DRM d’Adobe Primetime pour la protection du contenu*.

Si votre application serveur est basée sur l’implémentation de référence DRM Primetime, vous n’avez pas à mettre à jour votre  côté serveur. Le `flashaccess-refimpl.properties` fichier contient des champs dans lesquels vous pouvez spécifier des certificats de serveur de transport et de licence supplémentaires. Si vous n’avez qu’un seul certificat, vous n’avez pas à renseigner ces propriétés. Si vous avez des certificats expirés et que vous souhaitez utiliser ces certificats lorsque vous publiez des réponses de licence, vous devez les fournir au fichier de configuration et redémarrer votre serveur.

Pour spécifier d’anciens certificats, utilisez les propriétés suivantes :

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`

