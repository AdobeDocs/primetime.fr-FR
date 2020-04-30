---
seo-title: Migration de FMRMS 1.0 ou 1.5 vers Adobe Access 2.0 et versions ultérieures
title: Migration de FMRMS 1.0 ou 1.5 vers Adobe Access 2.0 et versions ultérieures
uuid: 05caeb39-0c62-4053-87a9-8e89030a188d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Migration de FMRMS 1.0 ou 1.5 vers Adobe Access 2.0 et versions ultérieures {#migrating-from-fmrms-or-to-adobe-access-and-above}

Pour continuer à émettre des licences pour le contenu compressé à l’aide de Flash Media Rights Management Server (FMRMS) 1.0 ou 1.5, les données de licence et de stratégie doivent être migrées du serveur LiveCycle ES vers le nouveau serveur du client en fonction du SDK Adobe Access. Les étapes importantes sont les suivantes :

1. Importation des informations de licence
1. Conversion de stratégies FMRMS au format Adobe Access
1. Prise en charge des demandes de compatibilité 1.x via le `FMRMSv1RequestHandler` et `FMRMSv1MetadataHandler`

Pour importer les informations de licence de LiveCycle ES dans votre serveur Adobe Access, reportez-vous aux exemples de scripts de base de données fournis dans le [!DNL Reference Implementation\Server\migration\db] dossier. Des exemples de scripts sont fournis pour l’exportation des données pertinentes d’une base de données MySQL, Oracle ou SQL Server au format de fichier CSV. Une fois les données exportées, elles peuvent être importées dans la base de données de votre choix. Les informations de licence exportées comprennent l’ID de licence, un ID de contenu affecté au moment du pack, l’ID de la stratégie utilisée, l’heure du pack du contenu et la clé de chiffrement du contenu. Pour Adobe Access, ces informations sont requises pour convertir les métadonnées de contenu 1.x au format de métadonnées Adobe Access (voir `FMRMSv1RequestHandler` et `FMRMSv1MetadataHandler`). Dans l’implémentation de référence, ces données sont stockées dans la table de la base de données License et utilisées par `RefImplMetadataConvReqHandler`.

Les stratégies existantes devront être converties au format Adobe Access afin d’utiliser ces stratégies lors de la conversion de métadonnées et de l’émission de licences pour du contenu 1.0 ou 1.5. Le document de référence Implementation\Server\migration folder contains sample code for creating an Adobe Access policy based on older policies.

Si vous effectuez une migration de FMRMS 1.0 vers Adobe Access, reportez-vous à l’exemple V1_0PolicyConverter.java. Compilez l’exemple de code en exécutant &quot; `ant-f build-migration.xml build-1.0-converter`&quot; (le script s’attend à ce que les bibliothèques 1.0 et Adobe Access se trouvent dans [!DNL libs/1.0] libs/flashaccess, respectivement). Modifiez le fichier converter.properties pour qu’il pointe vers votre serveur LiveCycle ES. Exécutez ensuite &quot; `ant -f build-migration.xml migrate-all-1.0-policies`&quot; pour convertir toutes les stratégies FMRMS 1.0 au format Adobe Access.

Si vous effectuez une migration de FMRMS 1.5 vers Adobe Access, reportez-vous à l’exemple V1_5PolicyConverter.java. Compilez l&#39;exemple de code en exécutant &quot; `ant-f build-migration.xml build-1.5-converter`&quot; (le script s&#39;attend à ce que les bibliothèques 1.5 et 3.0 soient respectivement dans libs/1.5 et libs/flashaccess). Modifiez le fichier converter.properties pour qu’il pointe vers votre serveur LiveCycle ES. Exécutez ensuite &quot; `ant -f build-migration.xml migrate-all-1.5-policies`&quot; pour convertir toutes les stratégies FMRMS 1.5 au format Adobe Access.

Les stratégies converties seront écrites dans un ensemble de fichiers. En outre, PolicyConverter génère un fichier CSV contenant le mappage des anciens ID de stratégie avec les nouveaux ID de stratégie. Ce fichier peut être importé dans la table &quot;PolicyConversion&quot; de la base de données d&#39;implémentation des références et sera utilisé par `RefImplMetadataConvReqHandler`les.

Une fois que les données pertinentes ont été migrées vers votre serveur Adobe Access, vous êtes prêt à mettre en oeuvre la prise en charge des demandes de compatibilité 1.x. Voir `RefImplUpgradeV1ClientHandler` et `RefImplMetadataConvReqHandler` dans l’implémentation des références pour obtenir des exemples de traitement de ces types de requêtes.
