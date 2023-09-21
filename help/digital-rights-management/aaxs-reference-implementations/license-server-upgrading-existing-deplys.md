---
title: Mise à niveau des déploiements existants
description: Mise à niveau des déploiements existants
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Mise à niveau des déploiements existants {#upgrading-existing-deployments}

Pour mettre à niveau un serveur exécutant la version 3.0 Reference Implementation License Server ou Watched Folder Packager, remplacez la variable [!DNL .war] les fichiers déployés sur votre serveur d’applications avec les fichiers inclus avec le serveur de mise en oeuvre de référence d’accès Adobe.

Si vous prévoyez d’utiliser l’enregistrement de domaine avec le serveur de licence d’implémentation de référence, plusieurs nouvelles tables de base de données sont requises. Pour recréer l’intégralité de la base de données d’implémentation de référence, exécutez `CreateSampleDB.sql`. Pour conserver les enregistrements de base de données existants et ajouter les nouvelles tables, ouvrez `CreateSampleDB.sql`et exécutez uniquement les commandes pour créer les tableaux suivants :

* `DomainServerInfo`
* `DomainKeys`
* `DomainMembership`
* `UserDomainMembership`
* `UserDomainRefCount`

Les propriétés suivantes doivent être ajoutées à flashaccess-refimpl.properties pour utiliser la prise en charge du domaine :

* `HandlerConfiguration.DomainCAs.n` ou `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

* `Domain RegistrationHandler.ServerCredential` et `DomainRegistrationHandler.ServerCredential.password`, ou `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

* `DomainRegistrationHandler.DomainServerUrl`

Les propriétés suivantes doivent être ajoutées à [!DNL flashaccess-refimpl.properties] pour prendre en charge la diffusion à distance par clé aux clients iOS :

* `HandlerConfiguration.KeyServerCertificate` ou `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`
