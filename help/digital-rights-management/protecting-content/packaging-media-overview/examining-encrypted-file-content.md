---
seo-title: Examen du contenu des fichiers chiffrés
title: Examen du contenu des fichiers chiffrés
uuid: 1b3318f6-0850-43f2-9127-c72ea81a1bdf
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Examen du contenu du fichier chiffré{#examining-encrypted-file-content}

Vous pouvez examiner le contenu d’un fichier multimédia chiffré à l’aide de l’API Java.

Pour examiner le contenu des fichiers chiffrés :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR. Voir *Configuration du SDK* pour votre projet.
1. Créez une instance `MediaEncrypter`.
1. Transmettez le fichier chiffré à la méthode `MediaEncrypter.examineEncryptedContent`, qui renvoie un objet `KeyMetaData`.

1. Inspect les informations dans l&#39;objet `KeyMetaData`.

Pour obtenir un exemple de code décrivant comment extraire des métadonnées DRM d’un fichier chiffré, voir `com.adobe.flashaccess.samples.mediapackager.ExamineContent` dans le répertoire Reference Implementation Command Line Tools [!DNL samples/].
