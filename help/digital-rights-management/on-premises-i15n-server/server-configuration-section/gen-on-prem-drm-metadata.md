---
title: Génération des métadonnées DRM On Premise
description: Génération des métadonnées DRM On Premise
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Génération des métadonnées DRM On Premise{#generate-the-on-premises-drm-metadata}

A [!DNL CreateMetadata.jar] est inclus dans la variable [!DNL create_metadata] dossier. L’objectif de cet utilitaire est de créer des métadonnées DRM On Premise qui inciteront le client à exécuter le processus d’individualisation sur le serveur d’individualisation On Premise spécifié.

1. Mettez à jour la mise en oeuvre de référence DRM Primetime - Outils de ligne de commande avec les fichiers suivants :

   * [!DNL CreateMetadata.jar]
   * [!DNL commons-cli-1.2.jar]
   * [!DNL createMetadata.properties]

     Les deux fichiers JAR peuvent se trouver dans la variable [!DNL Command Line Tools/libs] dossier. La variable [!DNL createMetadata.properties] peut se trouver à côté du fichier [!DNL flashaccesstools.properties] fichier .

<!--<a id="example_2116349CA33642CD9293EAD94A532ED8"></a>-->

Inclus est un [!DNL examplecreate.sh] script qui illustre un exemple de création de métadonnées. Veillez à configurer l’URL du serveur de licences et l’URL du serveur d’individualisation dans les fichiers de script et de propriétés avant de tenter de générer des métadonnées.

Les entrées pour l’utilitaire sont les suivantes :

* `createMetadata.properties` - Fichier de propriétés contenant une stratégie par défaut, les emplacements et mots de passe des certificats, etc.
* `indivCert` - Fichier PKCS12 contenant le certificat de transport d’individualisation
* `indivURL` - URL du serveur d’individualisation On Premise

Le fichier de sortie est un fichier de métadonnées DRM On Premise qui sera utilisé par le client DRM. Par exemple :

```
java -jar libs/CreateMetadata.jar -c createMetadata.properties -indivCert i15n_transport.cer
-indivURL https://[YOURINDIVSERVER:PORT] onpremdrm.metadata
```

.
