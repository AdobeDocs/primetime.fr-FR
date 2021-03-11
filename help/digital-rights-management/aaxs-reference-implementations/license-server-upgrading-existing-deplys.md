---
title: Mise à niveau des déploiements existants
description: Mise à niveau des déploiements existants
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Mise à niveau des déploiements existants {#upgrading-existing-deployments}

Pour mettre à niveau un serveur exécutant la version 3.0 Reference Implementation License Server ou Watched Folder Packager, remplacez les fichiers [!DNL .war] déployés sur votre serveur d’applications par les fichiers inclus avec le serveur de mise en oeuvre de référence d’accès aux Adobes.

Si vous prévoyez d’utiliser l’enregistrement de domaine avec le serveur de licences d’implémentation de référence, plusieurs nouvelles tables de base de données sont requises. Pour recréer l&#39;intégralité de la base de données d&#39;implémentation de référence, exécutez `CreateSampleDB.sql`. Pour conserver les enregistrements de base de données existants et ajouter les nouvelles tables, ouvrez `CreateSampleDB.sql`et exécutez uniquement les commandes pour créer les tables suivantes :

* `DomainServerInfo`
* `DomainKeys`
* `DomainMembership`
* `UserDomainMembership`
* `UserDomainRefCount`

Les propriétés suivantes doivent être ajoutées à flashaccess-refimpl.properties pour utiliser la prise en charge des domaines :

* `HandlerConfiguration.DomainCAs.n` ou  `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

* `Domain RegistrationHandler.ServerCredential` et  `DomainRegistrationHandler.ServerCredential.password`ou  `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

* `DomainRegistrationHandler.DomainServerUrl`

Les propriétés suivantes doivent être ajoutées à [!DNL flashaccess-refimpl.properties] pour prendre en charge la diffusion des clés distantes sur les clients iOS :

* `HandlerConfiguration.KeyServerCertificate` ou  `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`

