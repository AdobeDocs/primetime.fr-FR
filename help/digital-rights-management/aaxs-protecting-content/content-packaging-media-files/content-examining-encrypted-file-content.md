---
seo-title: Examen du contenu des fichiers chiffrés
title: Examen du contenu des fichiers chiffrés
uuid: 2132fac7-5f11-4308-b511-ed4f216527a6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Examen du contenu des fichiers chiffrés {#examining-encrypted-file-content}

Pour examiner le contenu d’un fichier FLV ou F4V à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans [Configuration de l’environnement](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) de développement dans votre projet.
1. Créez une `MediaEncrypter` instance.
1. Transmettez le fichier chiffré à la `MediaEncrypter.examineEncryptedContent` méthode, qui renvoie un `KeyMetaData` objet.
1. Examinez les informations contenues dans l’ `KeyMetaData` objet.

Pour obtenir un exemple de code montrant comment extraire les métadonnées DRM d’un fichier chiffré, voir `com.adobe.flashaccess.samples.mediapackager.ExamineContent` dans le répertoire &quot;samples&quot; des outils de ligne de commande de mise en oeuvre de référence.
