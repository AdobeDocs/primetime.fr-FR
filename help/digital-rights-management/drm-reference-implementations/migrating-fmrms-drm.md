---
description: Pour continuer à émettre des licences pour le contenu qui a été inclus avec Flash Media Rights Management Server (FMRMS) 1.0 ou 1.5, vous devez migrer les données de licence et de stratégie DRM du serveur LiveCycle ES vers le nouveau serveur du client, basé sur le SDK DRM Adobe Primetime.
seo-description: Pour continuer à émettre des licences pour le contenu qui a été inclus avec Flash Media Rights Management Server (FMRMS) 1.0 ou 1.5, vous devez migrer les données de licence et de stratégie DRM du serveur LiveCycle ES vers le nouveau serveur du client, basé sur le SDK DRM Adobe Primetime.
seo-title: Migration de FMRMS 1.0 ou 1.5 vers Adobe Primetime DRM 2.0 ou version ultérieure
title: Migration de FMRMS 1.0 ou 1.5 vers Adobe Primetime DRM 2.0 ou version ultérieure
uuid: 49ecbbd2-d83b-4bf2-841e-c3f9e5d5e141
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# Migration de FMRMS 1.0 ou 1.5 vers Adobe Primetime DRM 2.0 ou version ultérieure{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

Pour continuer à émettre des licences pour le contenu qui a été inclus avec Flash Media Rights Management Server (FMRMS) 1.0 ou 1.5, vous devez migrer les données de licence et de stratégie DRM du serveur LiveCycle ES vers le nouveau serveur du client, basé sur le SDK DRM Adobe Primetime.

Pour effectuer la migration, effectuez les tâches suivantes :

1. Importer les informations de licence :

   1. Pour importer des informations de licence de LiveCycle ES vers votre serveur DRM Primetime, reportez-vous aux exemples de scripts de base de données du dossier [!DNL Reference Implementation\Server\migration\db].
   1. Exécutez les exemples de scripts pour exporter les données appropriées d’une base de données MySQL, Oracle ou SQL Server vers un format de fichier CSV.
   1. Après avoir exporté les données du LiveCycle ES, importez-les dans votre base de données.

      Les informations de licence exportées comprennent les éléments suivants :

      * Un ID de licence
      * ID de contenu affecté au moment du pack
      * ID de la stratégie DRM appliquée
      * Heure à laquelle le contenu a été assemblé
      * La clé de chiffrement du contenu

      Ces informations sont requises avant de pouvoir convertir les métadonnées de contenu 1.x au format de métadonnées DRM Primetime. Dans l&#39;implémentation de référence, ces données sont stockées dans la table de base de données License et sont utilisées par `RefImplMetadataConvReqHandler`. Pour plus d&#39;informations, voir `FMRMSv1RequestHandler` et `FMRMSv1MetadataHandler`.


1. Convertir les stratégies FMRMS au format DRM Primetime :

   1. Avant de pouvoir appliquer les stratégies DRM pour convertir les métadonnées et émettre des licences pour le contenu de la version 1.0 ou 1.5, convertissez les stratégies DRM existantes au format DRM Primetime.

      Le dossier `Reference Implementation\Server\migration` contient un exemple de code pour créer une stratégie DRM Primetime basée sur des stratégies DRM plus anciennes. Pour migrer de FMRMS 1.0 vers Primetime DRM, consultez l&#39;exemple `V1_0PolicyConverter.java`.
   1. Compilez l’exemple de code en exécutant le script `ant-f build-migration.xml build-1.0-converter` qui recherche les bibliothèques DRM 1.0 et Primetime dans les répertoires [!DNL libs/1.0] et [!DNL libs/flashaccess].

   1. Modifiez le fichier [!DNL converter.properties] pour pointer vers votre serveur LiveCycle ES.
   1. Exécutez `ant -f build-migration.xml migrate-all-1.0-policies` pour convertir toutes les stratégies DRM FMRMS 1.0 au format DRM Primetime.

      Pour migrer de FMRMS 1.5 vers Primetime DRM, consultez l&#39;exemple `V1_5PolicyConverter.java`.

   1. Compilez l’exemple de code en exécutant le script `ant-f build-migration.xml build-1.5-converter`, qui prévoit que les bibliothèques 1.5 et 3.0 se trouvent dans les répertoires [!DNL libs/1.5] et [!DNL libs/flashaccess].

   1. Modifiez le fichier [!DNL converter.properties] pour pointer vers votre serveur LiveCycle ES.
   1. Exécutez `ant -f build-migration.xml migrate-all-1.5-policies` pour convertir toutes les stratégies DRM FMRMS 1.5 au format DRM Primetime.

      Les stratégies DRM converties sont enregistrées sous la forme d’un ensemble de fichiers. `DRM PolicyConverter` génère un fichier au format CSV qui inclut le mappage des anciens ID de stratégie DRM aux nouveaux ID de stratégie DRM. Vous pouvez importer ce fichier dans la table [!DNL PolicyConversion] de la base de données d&#39;implémentation de référence, où il est utilisé par `RefImplMetadataConvReqHandler`.

1. Prise en charge des demandes de compatibilité 1.x avec les propriétés `FMRMSv1RequestHandler` et `FMRMSv1MetadataHandler` :

   1. Une fois les données pertinentes migrées vers un serveur DRM Primetime, mettez en oeuvre la prise en charge des demandes de compatibilité 1.x.

      Pour obtenir des exemples sur la façon de traiter ces types de requêtes, voir `RefImplUpgradeV1ClientHandler` et `RefImplMetadataConvReqHandler` dans l’implémentation de référence.

