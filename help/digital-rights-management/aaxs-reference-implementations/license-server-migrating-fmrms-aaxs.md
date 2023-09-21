---
title: Migration de FMRMS 1.0 ou 1.5 vers Adobe Access 2.0 et versions ultérieures
description: Migration de FMRMS 1.0 ou 1.5 vers Adobe Access 2.0 et versions ultérieures
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Migration de FMRMS 1.0 ou 1.5 vers Adobe Access 2.0 et versions ultérieures {#migrating-from-fmrms-or-to-adobe-access-and-above}

Pour continuer à émettre des licences pour le contenu empaqueté à l’aide du Flash Media Rights Management Server (FMRMS) 1.0 ou 1.5, les données de licence et de stratégie doivent être migrées du serveur ES de LiveCycle vers le nouveau serveur du client en fonction du SDK Adobe Access. Les étapes importantes sont les suivantes :

1. Importer des informations de licence
1. Conversion des stratégies FMRMS au format Adobe Access
1. Prise en charge des demandes de compatibilité 1.x via le `FMRMSv1RequestHandler` et `FMRMSv1MetadataHandler`

Pour importer des informations de licence de LiveCycle ES dans votre serveur Adobe basé sur les accès, reportez-vous aux exemples de scripts de base de données fournis dans la section [!DNL Reference Implementation\Server\migration\db] dossier. Des exemples de scripts sont fournis pour exporter les données pertinentes d’une base de données MySQL, Oracle ou SQL Server vers un format de fichier CSV. Une fois les données exportées, elles peuvent être importées dans la base de données de votre choix. Les informations de licence exportées incluent l’ID de licence, un ID de contenu attribué au moment du conditionnement, l’ID de la stratégie utilisée, l’heure à laquelle le contenu a été compressé et la clé de chiffrement du contenu. Pour l’accès aux Adobes, ces informations sont requises afin de convertir les métadonnées de contenu 1.x au format de métadonnées d’accès aux Adobes (voir `FMRMSv1RequestHandler` et `FMRMSv1MetadataHandler`). Dans l’implémentation de référence, ces données sont stockées dans le tableau de la base de données de licence et utilisées par `RefImplMetadataConvReqHandler`.

Les stratégies existantes devront être converties au format Adobe Access afin d’utiliser ces stratégies lors de la conversion de métadonnées et de l’octroi de licences pour le contenu 1.0 ou 1.5. Le dossier Reference Implementation\Server\migration contient un exemple de code pour créer une stratégie Adobe Access basée sur des stratégies plus anciennes.

Si vous effectuez une migration de FMRMS 1.0 vers Adobe Access, reportez-vous à l’exemple V1_0PolicyConverter.java . Compilez l’exemple de code en exécutant &quot; `ant-f build-migration.xml build-1.0-converter`&quot; (le script s’attend à ce que les bibliothèques d’accès 1.0 et Adobe soient dans [!DNL libs/1.0] et libs/flashaccess, respectivement). Modifiez le fichier converter.properties pour pointer vers votre serveur LiveCycle ES. Exécutez ensuite &quot; `ant -f build-migration.xml migrate-all-1.0-policies`&quot; pour convertir toutes les stratégies FMRMS 1.0 au format Adobe Access.

Si vous effectuez une migration de FMRMS 1.5 vers Adobe Access, reportez-vous à l’exemple V1_5PolicyConverter.java . Compilez l’exemple de code en exécutant &quot; `ant-f build-migration.xml build-1.5-converter`&quot; (le script s’attend à ce que les bibliothèques 1.5 et 3.0 se trouvent respectivement dans libs/1.5 et libs/flashaccess). Modifiez le fichier converter.properties pour pointer vers votre serveur LiveCycle ES. Exécutez ensuite &quot; `ant -f build-migration.xml migrate-all-1.5-policies`&quot; pour convertir toutes les stratégies FMRMS 1.5 au format Adobe Access.

Les stratégies converties seront écrites dans un ensemble de fichiers. En outre, PolicyConverter génère un fichier CSV contenant le mappage des anciens identifiants de stratégie sur les nouveaux identifiants de stratégie. Ce fichier peut être importé dans la table &quot;PolicyConversion&quot; de la base de données d’implémentation de référence et sera utilisé par `RefImplMetadataConvReqHandler`.

Une fois que les données appropriées ont été migrées vers votre serveur Adobe basé sur l’accès, vous êtes prêt à mettre en oeuvre la prise en charge des demandes de compatibilité 1.x. Voir `RefImplUpgradeV1ClientHandler` et `RefImplMetadataConvReqHandler` dans l’implémentation de référence pour obtenir des exemples de traitement de ces types de requêtes.
