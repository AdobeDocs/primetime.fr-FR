---
seo-title: Examen du contenu des fichiers chiffrés
title: Examen du contenu des fichiers chiffrés
uuid: 1b3318f6-0850-43f2-9127-c72ea81a1bdf
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Examen du contenu des fichiers chiffrés{#examining-encrypted-file-content}

Vous pouvez examiner le contenu d’un fichier multimédia chiffré à l’aide de l’API Java.

Pour examiner le contenu des fichiers chiffrés :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR. Voir *Configuration du SDK* pour votre projet.
1. Créez une `MediaEncrypter` instance.
1. Transmettez le fichier chiffré à la `MediaEncrypter.examineEncryptedContent` méthode, qui renvoie un `KeyMetaData` objet.

1. Examinez les informations contenues dans l’ `KeyMetaData` objet.

Pour obtenir un exemple de code qui décrit comment extraire des métadonnées DRM d’un fichier chiffré, voir `com.adobe.flashaccess.samples.mediapackager.ExamineContent` dans le [!DNL samples/] répertoire Reference Implementation Command Line Tools (Outils de ligne de commande de mise en oeuvre de référence).
