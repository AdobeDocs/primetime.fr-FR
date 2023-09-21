---
title: Examen du contenu du fichier chiffré
description: Examen du contenu du fichier chiffré
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Examen du contenu du fichier chiffré {#examining-encrypted-file-content}

Pour examiner le contenu d’un fichier FLV ou F4V à l’aide de l’API Java, procédez comme suit :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR mentionnés dans [Configuration de l’environnement de développement](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) dans votre projet.
1. Créez un `MediaEncrypter` instance.
1. Transmettez le fichier chiffré à la variable `MediaEncrypter.examineEncryptedContent` , qui renvoie une `KeyMetaData` .
1. Inspect les informations dans la variable `KeyMetaData` .

Pour obtenir un exemple de code montrant comment extraire des métadonnées DRM d’un fichier chiffré, voir `com.adobe.flashaccess.samples.mediapackager.ExamineContent` dans le répertoire &quot;Exemples&quot; des outils de ligne de commande de mise en oeuvre de référence.
