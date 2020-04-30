---
description: Pour continuer à émettre des licences pour le contenu qui a été inclus dans le pack avec Flash Media Rights Management Server (FMRMS) 1.0 ou 1.5, vous devez migrer les données de licence et de stratégie DRM du serveur LiveCycle ES vers le nouveau serveur du client, basé sur le SDK DRM d’Adobe Primetime.
seo-description: Pour continuer à émettre des licences pour le contenu qui a été inclus dans le pack avec Flash Media Rights Management Server (FMRMS) 1.0 ou 1.5, vous devez migrer les données de licence et de stratégie DRM du serveur LiveCycle ES vers le nouveau serveur du client, basé sur le SDK DRM d’Adobe Primetime.
seo-title: Migration de FMRMS 1.0 ou 1.5 vers Adobe Primetime DRM 2.0 ou version ultérieure
title: Migration de FMRMS 1.0 ou 1.5 vers Adobe Primetime DRM 2.0 ou version ultérieure
uuid: 49ecbbd2-d83b-4bf2-841e-c3f9e5d5e141
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Migration de FMRMS 1.0 ou 1.5 vers Adobe Primetime DRM 2.0 ou version ultérieure{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

Pour continuer à émettre des licences pour le contenu qui a été inclus dans le pack avec Flash Media Rights Management Server (FMRMS) 1.0 ou 1.5, vous devez migrer les données de licence et de stratégie DRM du serveur LiveCycle ES vers le nouveau serveur du client, basé sur le SDK DRM d’Adobe Primetime.

Pour effectuer la migration, effectuez les tâches suivantes :

1. Importer les informations de licence :

   1. Pour importer des informations de licence de LiveCycle ES vers votre serveur DRM Primetime, reportez-vous aux exemples de scripts de base de données du [!DNL Reference Implementation\Server\migration\db] dossier.
   1. Exécutez les exemples de scripts pour exporter les données appropriées d’une base de données MySQL, Oracle ou SQL Server vers un format de fichier CSV.
   1. Après avoir exporté les données de LiveCycle ES, importez-les dans votre base de données.

      Les informations de licence exportées comprennent les éléments suivants :

      * Un ID de licence
      * ID de contenu affecté au moment du pack
      * ID de la stratégie DRM appliquée
      * Heure à laquelle le contenu a été assemblé
      * La clé de chiffrement du contenu
      Ces informations sont requises avant de pouvoir convertir les métadonnées de contenu 1.x au format de métadonnées DRM Primetime. Dans l’implémentation de référence, ces données sont stockées dans la table de la base de données License et sont utilisées par `RefImplMetadataConvReqHandler`. For more information, see `FMRMSv1RequestHandler` and `FMRMSv1MetadataHandler`.


1. Convertir les stratégies FMRMS au format DRM Primetime :

   1. Avant de pouvoir appliquer les stratégies DRM pour convertir les métadonnées et émettre des licences pour le contenu de la version 1.0 ou 1.5, convertissez les stratégies DRM existantes au format DRM Primetime.

      Le `Reference Implementation\Server\migration` dossier comprend un exemple de code pour créer une stratégie DRM Primetime basée sur des stratégies DRM plus anciennes. Pour migrer de FMRMS 1.0 vers Primetime DRM, consultez l’ `V1_0PolicyConverter.java` exemple.
   1. Compilez l’exemple de code en exécutant `ant-f build-migration.xml build-1.0-converter` un script, qui recherche les bibliothèques DRM 1.0 et Primetime dans les [!DNL libs/1.0] répertoires et [!DNL libs/flashaccess] .

   1. Modifiez le [!DNL converter.properties] fichier pour qu’il pointe vers votre serveur LiveCycle ES.
   1. Exécutez `ant -f build-migration.xml migrate-all-1.0-policies` pour convertir toutes les stratégies DRM FMRMS 1.0 au format DRM Primetime.

      Pour migrer de FMRMS 1.5 vers Primetime DRM, consultez l’ `V1_5PolicyConverter.java` exemple.

   1. Compilez l’exemple de code en exécutant `ant-f build-migration.xml build-1.5-converter` un script, qui prévoit que les bibliothèques 1.5 et 3.0 se trouvent dans les [!DNL libs/1.5] répertoires et [!DNL libs/flashaccess] .

   1. Modifiez le [!DNL converter.properties] fichier pour qu’il pointe vers votre serveur LiveCycle ES.
   1. Exécutez `ant -f build-migration.xml migrate-all-1.5-policies` pour convertir toutes les stratégies DRM FMRMS 1.5 au format DRM Primetime.

      Les stratégies DRM converties sont enregistrées sous la forme d’un ensemble de fichiers. Le fichier `DRM PolicyConverter` génère un fichier au format CSV qui inclut le mappage des anciens ID de stratégie DRM aux nouveaux ID de stratégie DRM. Vous pouvez importer ce fichier dans la [!DNL PolicyConversion] table de la base de données d’implémentation de référence, où il est utilisé par `RefImplMetadataConvReqHandler`les.

1. Prise en charge des demandes de compatibilité 1.x avec les `FMRMSv1RequestHandler` et `FMRMSv1MetadataHandler` propriétés :

   1. Une fois les données pertinentes migrées vers un serveur DRM Primetime, mettez en oeuvre la prise en charge des demandes de compatibilité 1.x.

      Pour obtenir des exemples sur le traitement de ces types de requêtes, voir et `RefImplUpgradeV1ClientHandler` `RefImplMetadataConvReqHandler` dans l’implémentation des références.

