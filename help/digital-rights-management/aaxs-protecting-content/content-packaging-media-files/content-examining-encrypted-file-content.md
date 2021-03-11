---
title: Examen du contenu des fichiers chiffrés
description: Examen du contenu des fichiers chiffrés
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Examen du contenu du fichier chiffré {#examining-encrypted-file-content}

Pour examiner le contenu d’un fichier FLV ou F4V à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans [Configuration de l&#39;environnement de développement](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) dans votre projet.
1. Créez une instance `MediaEncrypter`.
1. Transmettez le fichier chiffré à la méthode `MediaEncrypter.examineEncryptedContent`, qui renvoie un objet `KeyMetaData`.
1. Inspect les informations dans l&#39;objet `KeyMetaData`.

Pour obtenir un exemple de code montrant comment extraire les métadonnées DRM d&#39;un fichier chiffré, voir `com.adobe.flashaccess.samples.mediapackager.ExamineContent` dans le répertoire Reference Implementation Command Line Tools &quot;samples&quot;.
