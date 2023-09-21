---
title: Renouvellement des certificats
description: Renouvellement des certificats
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Renouvellement des certificats{#renew-certificates}

Vous devez connaître les restrictions de renouvellement de certificat suivantes, basées sur votre configuration de SDK DRM Adobe Primetime :

* SDK de production DRM Primetime

  Adobe fournit l’ensemble initial de certificats gratuits pour le SDK de production Primetime DRM lorsque vous achetez un contrat d’assistance. Si vous ne disposez pas d’un contrat d’assistance, vous pouvez acheter un ensemble de certificats de renouvellement valides pour deux ans.
* SDK d’évaluation DRM Primetime

  Le jeu de certificats de ce SDK est valide pendant un an et ne peut pas être renouvelé.
* SDK d’évaluation DRM Primetime

  Le SDK d’évaluation DRM Primetime est valide pendant trois mois et Adobe fournit un ensemble de certificats de renouvellement gratuits.

## Mise en oeuvre de nouveaux certificats et utilisation d’anciens certificats pour du contenu existant {#section_345C92D1C9794B0BBB9A9B0702EC95FF}

Dans Primetime DRM, vous pouvez autoriser un serveur de licences à émettre une licence pour le contenu empaqueté avec des certificats de package précédents (ou même expirés). Pour configurer votre serveur de manière à accepter les demandes de licence provenant de contenu précédemment compilé, fournissez votre ancien certificat à votre serveur et mettez à jour le fichier de configuration de votre serveur afin que le serveur sache où trouver les anciens certificats. Pour plus d’informations, voir *Gestion des mises à jour de certificat lors de l’expiration des certificats émis par un Adobe* in *Utilisation du SDK Adobe Primetime DRM pour la protection du contenu*.

Si votre application serveur est basée sur la mise en oeuvre de référence DRM Primetime, il n’est pas nécessaire de mettre à jour votre programme côté serveur. Dans le `flashaccess-refimpl.properties` , il existe des champs dans lesquels vous pouvez spécifier des certificats de transport et de serveur de licences supplémentaires. Si vous ne disposez que d’un seul certificat, il n’est pas nécessaire de renseigner ces propriétés. Si vous avez expiré des certificats et que vous souhaitez utiliser ces certificats lorsque vous envoyez des réponses de licence, vous devez fournir ces certificats au fichier de configuration et redémarrer votre serveur.

Pour spécifier d’anciens certificats, utilisez les propriétés suivantes :

* `#HandlerConfiguration.AdditionalServerTransportCredential.1=transport.pfx`
* `#HandlerConfiguration.AdditionalServerTransportCredential.1.password=[password]`
* `#AsymmetricKeyRetrieval.ServerCredential.1=license_server.pfx`
* `#AsymmetricKeyRetrieval.ServerCredential.1.password=[password]`
