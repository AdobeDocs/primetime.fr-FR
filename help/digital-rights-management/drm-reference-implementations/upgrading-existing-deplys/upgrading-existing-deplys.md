---
description: Pour mettre à niveau un serveur prenant en charge le serveur de licence d’implémentation de référence version 3.0 ou Watched Folder Packager, vous devez remplacer les fichiers .war qui ont été déployés sur un serveur d’applications par les fichiers qui ont été inclus avec Adobe Primetime DRM Reference Implementation Server.
seo-description: Pour mettre à niveau un serveur prenant en charge le serveur de licence d’implémentation de référence version 3.0 ou Watched Folder Packager, vous devez remplacer les fichiers .war qui ont été déployés sur un serveur d’applications par les fichiers qui ont été inclus avec Adobe Primetime DRM Reference Implementation Server.
seo-title: Mettre à niveau les déploiements existants
title: Mettre à niveau les déploiements existants
uuid: 1a40aae9-f639-41fa-b42d-cf8cdfcde694
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Présentation {#upgrade-existing-deployments-overview}

Pour mettre à niveau un serveur prenant en charge le serveur de licence d’implémentation de référence version 3.0 ou Watched Folder Packager, vous devez remplacer les fichiers .war qui ont été déployés sur un serveur d’applications par les fichiers qui ont été inclus avec Adobe Primetime DRM Reference Implementation Server.

Pour utiliser l’enregistrement de domaine avec le serveur de licence d’implémentation de référence, plusieurs nouvelles tables de base de données sont requises. Vous devez recréer l’intégralité de la base de données d’implémentation de référence et l’exécuter `CreateSampleDB.sql`.

Pour conserver les enregistrements de base de données et ajouter de nouvelles tables :

1. Ouvrez `CreateSampleDB.sql` et exécutez des commandes qui créent les tableaux suivants :

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. Ajouter les propriétés suivantes pour [!DNL flashaccess-refimpl.properties] utiliser la prise en charge des domaines :

   * `HandlerConfiguration.DomainCAs.n` ou `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` et `DomainRegistrationHandler.ServerCredential.password` ou `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. Ajouter les propriétés suivantes pour [!DNL flashaccess-refimpl.properties] prendre en charge la diffusion de clés distantes pour les clients iOS :

   * `HandlerConfiguration.KeyServerCertificate` ou `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`