---
description: Pour continuer à émettre des licences pour le contenu qui a été compilé avec le Flash Media Rights Management Server (FMRMS) 1.0 ou 1.5, vous devez migrer les données de licence et de stratégie DRM du serveur LiveCycle ES vers le nouveau serveur du client basé sur le SDK Adobe Primetime DRM.
title: Migration de FMRMS 1.0 ou 1.5 vers Adobe Primetime DRM 2.0 ou version ultérieure
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Migration de FMRMS 1.0 ou 1.5 vers Adobe Primetime DRM 2.0 ou version ultérieure{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

Pour continuer à émettre des licences pour le contenu qui a été compilé avec le Flash Media Rights Management Server (FMRMS) 1.0 ou 1.5, vous devez migrer les données de licence et de stratégie DRM du serveur LiveCycle ES vers le nouveau serveur du client basé sur le SDK Adobe Primetime DRM.

Pour effectuer la migration, effectuez les tâches suivantes :

1. Importer les informations de licence :

   1. Pour importer des informations de licence de LiveCycle ES vers votre serveur basé sur Primetime DRM, reportez-vous aux exemples de scripts de base de données dans la section [!DNL Reference Implementation\Server\migration\db] dossier.
   1. Exécutez les exemples de scripts pour exporter les données pertinentes d’une base de données MySQL, Oracle ou SQL Server vers un format de fichier CSV.
   1. Après avoir exporté les données du LiveCycle ES, importez les données dans votre base de données.

      Les informations de licence exportées sont les suivantes :

      * Un ID de licence
      * Identifiant de contenu attribué au moment du conditionnement
      * ID de la stratégie DRM appliquée
      * Heure à laquelle le contenu a été compressé
      * Clé de chiffrement du contenu

      Ces informations sont requises avant de pouvoir convertir les métadonnées de contenu 1.x au format de métadonnées DRM Primetime. Dans l’implémentation de référence, ces données sont stockées dans la table de la base de données de licence et sont utilisées par `RefImplMetadataConvReqHandler`. Pour plus d’informations, voir `FMRMSv1RequestHandler` et `FMRMSv1MetadataHandler`.

1. Convertissez les stratégies FMRMS au format Primetime DRM :

   1. Avant d’appliquer les stratégies DRM pour convertir des métadonnées et émettre des licences pour le contenu de la version 1.0 ou 1.5, convertissez les stratégies DRM existantes au format DRM Primetime.

      La variable `Reference Implementation\Server\migration` comprend un exemple de code pour créer une stratégie DRM Primetime basée sur des stratégies DRM plus anciennes. Pour migrer de FMRMS 1.0 à Primetime DRM , voir la section `V1_0PolicyConverter.java` exemple.
   1. Compilez l’exemple de code en exécutant `ant-f build-migration.xml build-1.0-converter` qui recherche les bibliothèques DRM 1.0 et Primetime dans le [!DNL libs/1.0] et [!DNL libs/flashaccess] répertoires.

   1. Modifiez la variable [!DNL converter.properties] pour pointer vers votre serveur ES de LiveCycle.
   1. Exécuter `ant -f build-migration.xml migrate-all-1.0-policies` pour convertir toutes les stratégies DRM FMRMS 1.0 au format Primetime DRM.

      Pour migrer de FMRMS 1.5 à Primetime DRM , reportez-vous à la section `V1_5PolicyConverter.java` exemple.

   1. Compilez l’exemple de code en exécutant `ant-f build-migration.xml build-1.5-converter` , ce qui suppose que les bibliothèques 1.5 et 3.0 se trouvent dans la variable [!DNL libs/1.5] et [!DNL libs/flashaccess] répertoires.

   1. Modifiez la variable [!DNL converter.properties] pour pointer vers votre serveur ES de LiveCycle.
   1. Exécuter `ant -f build-migration.xml migrate-all-1.5-policies` pour convertir toutes les stratégies DRM FMRMS 1.5 au format Primetime DRM.

      Les stratégies DRM converties sont enregistrées sous la forme d’un ensemble de fichiers. La variable `DRM PolicyConverter` génère un fichier au format CSV qui inclut le mappage des anciens identifiants de stratégie DRM aux nouveaux identifiants de stratégie DRM. Vous pouvez importer ce fichier dans le [!DNL PolicyConversion] dans la base de données d’implémentation de référence, où elle est utilisée par `RefImplMetadataConvReqHandler`.

1. Prise en charge des demandes de compatibilité 1.x avec la fonction `FMRMSv1RequestHandler` et `FMRMSv1MetadataHandler` properties:

   1. Une fois les données appropriées migrées vers un serveur basé sur Primetime DRM, mettez en oeuvre la prise en charge des demandes de compatibilité 1.x.

      Pour obtenir des exemples sur le traitement de ces types de requêtes, voir `RefImplUpgradeV1ClientHandler` et `RefImplMetadataConvReqHandler` dans l’implémentation de référence.
