---
seo-title: Générer les métadonnées DRM sur site
title: Générer les métadonnées DRM sur site
uuid: 89d53924-1a8d-42d4-a716-ce4f4566b6bf
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Générer les métadonnées DRM sur site{#generate-the-on-premises-drm-metadata}

Un [!DNL CreateMetadata.jar] utilitaire est inclus dans le [!DNL create_metadata] dossier. L’objectif de cet utilitaire est de créer des métadonnées DRM sur site qui permettront au client d’effectuer le processus d’individualisation par rapport au serveur d’individualisation sur site spécifié.

1. Mettez à jour la mise en oeuvre de référence DRM Primetime - Outils de ligne de commande avec les fichiers suivants :

   * [!DNL CreateMetadata.jar]
   * [!DNL commons-cli-1.2.jar]
   * [!DNL createMetadata.properties]

      Les deux fichiers JAR peuvent résider dans le [!DNL Command Line Tools/libs] dossier. Le [!DNL createMetadata.properties] fichier peut se trouver à côté du [!DNL flashaccesstools.properties] fichier.

<!--<a id="example_2116349CA33642CD9293EAD94A532ED8"></a>-->

Il s’agit d’un [!DNL examplecreate.sh] script présentant un exemple de création de métadonnées. Veillez à configurer l’URL du serveur de licences et l’URL du serveur d’individualisation dans le script et les fichiers de propriétés avant de tenter de générer des métadonnées.

Les entrées pour l&#39;utilitaire sont les suivantes :

* `createMetadata.properties` - Fichier de propriétés contenant une stratégie par défaut, des emplacements de certificats et des mots de passe, etc.
* `indivCert` - Fichier PKCS12 contenant le certificat de transport d&#39;individualisation
* `indivURL` - URL du serveur d&#39;individualisation local

Le fichier de sortie est un fichier de métadonnées DRM sur site qui sera utilisé par le client DRM. Par exemple :

```
java -jar libs/CreateMetadata.jar -c createMetadata.properties -indivCert i15n_transport.cer
-indivURL https://[YOURINDIVSERVER:PORT] onpremdrm.metadata
```

.