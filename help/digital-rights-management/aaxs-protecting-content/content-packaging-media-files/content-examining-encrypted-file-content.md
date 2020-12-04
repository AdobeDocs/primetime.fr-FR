---
seo-title: Examen du contenu des fichiers chiffrés
title: Examen du contenu des fichiers chiffrés
uuid: 2132fac7-5f11-4308-b511-ed4f216527a6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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
