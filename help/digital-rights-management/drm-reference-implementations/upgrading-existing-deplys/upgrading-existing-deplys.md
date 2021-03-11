---
description: Pour mettre à niveau un serveur prenant en charge le serveur de licence d’implémentation de référence version 3.0 ou Watched Folder Packager, vous devez remplacer les fichiers .war qui ont été déployés sur un serveur d’applications par les fichiers qui ont été inclus avec le serveur d’implémentation de référence DRM Adobe Primetime.
title: Mettre à niveau les déploiements existants
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Aperçu {#upgrade-existing-deployments-overview}

Pour mettre à niveau un serveur prenant en charge le serveur de licence d’implémentation de référence version 3.0 ou Watched Folder Packager, vous devez remplacer les fichiers .war qui ont été déployés sur un serveur d’applications par les fichiers qui ont été inclus avec le serveur d’implémentation de référence DRM Adobe Primetime.

Pour utiliser l’enregistrement de domaine avec le serveur de licence d’implémentation de référence, plusieurs nouvelles tables de base de données sont requises. Vous devez recréer l&#39;intégralité de la base de données d&#39;implémentation des références et exécuter `CreateSampleDB.sql`.

Pour conserver les enregistrements de base de données et ajouter de nouvelles tables :

1. Ouvrez `CreateSampleDB.sql` et exécutez des commandes qui créent les tableaux suivants :

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. Ajoutez les propriétés suivantes sur [!DNL flashaccess-refimpl.properties] pour utiliser la prise en charge du domaine :

   * `HandlerConfiguration.DomainCAs.n` ou  `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` et  `DomainRegistrationHandler.ServerCredential.password` ou  `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. Ajoutez les propriétés suivantes sur [!DNL flashaccess-refimpl.properties] pour prendre en charge la diffusion des clés distantes sur les clients iOS :

   * `HandlerConfiguration.KeyServerCertificate` ou  `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`