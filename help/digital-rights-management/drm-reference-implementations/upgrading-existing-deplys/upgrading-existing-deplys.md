---
description: Pour mettre à niveau un serveur prenant en charge la version 3.0 Reference Implementation License Server ou Watched Folder Packager, vous devez remplacer les fichiers .war qui ont été déployés sur un serveur d’applications par les fichiers qui ont été inclus avec Adobe Primetime DRM Reference Implementation Server.
title: Mettre à niveau les déploiements existants
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Présentation {#upgrade-existing-deployments-overview}

Pour mettre à niveau un serveur prenant en charge la version 3.0 Reference Implementation License Server ou Watched Folder Packager, vous devez remplacer les fichiers .war qui ont été déployés sur un serveur d’applications par les fichiers qui ont été inclus avec Adobe Primetime DRM Reference Implementation Server.

Pour utiliser l’enregistrement de domaine avec le serveur de licence de mise en oeuvre de référence, plusieurs nouvelles tables de base de données sont requises. Vous devez recréer l’intégralité de la base de données d’implémentation de référence et exécuter `CreateSampleDB.sql`.

Pour conserver les enregistrements de la base de données et ajouter de nouvelles tables :

1. Ouvrir `CreateSampleDB.sql` et exécutez les commandes qui créent les tableaux suivants :

   * `DomainServerInfo`
   * `DomainKeys`
   * `DomainMembership`
   * `UserDomainMembership`
   * `UserDomainRefCount`

1. Ajoutez les propriétés suivantes à [!DNL flashaccess-refimpl.properties] pour utiliser la prise en charge des domaines :

   * `HandlerConfiguration.DomainCAs.n` ou `RefImpl.HSM.HandlerConfiguration.DomainCAs.Alias.n`

   * `Domain RegistrationHandler.ServerCredential` et `DomainRegistrationHandler.ServerCredential.password` ou `RefImpl.HSM.DomainRegistrationHandler.ServerCredential.Alias`

   * `DomainRegistrationHandler.DomainServerUrl`

1. Ajoutez les propriétés suivantes à [!DNL flashaccess-refimpl.properties] pour prendre en charge la diffusion à distance par clé aux clients iOS :

   * `HandlerConfiguration.KeyServerCertificate` ou `RefImpl.HSM.HandlerConfiguration.KeyServerCertificate.Alias`
