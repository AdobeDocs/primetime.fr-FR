---
title: Examen du contenu du fichier chiffré
description: Examen du contenu du fichier chiffré
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# Examen du contenu du fichier chiffré{#examining-encrypted-file-content}

Vous pouvez examiner le contenu d’un fichier multimédia chiffré à l’aide de l’API Java.

Pour examiner le contenu d’un fichier chiffré :

1. Configurez votre environnement de développement et incluez tous les fichiers JAR. Voir *Configuration du SDK* pour votre projet.
1. Créez un `MediaEncrypter` instance.
1. Transmettez le fichier chiffré à la variable `MediaEncrypter.examineEncryptedContent` , qui renvoie une `KeyMetaData` .

1. Inspect les informations dans la variable `KeyMetaData` .

Pour obtenir un exemple de code qui décrit comment extraire des métadonnées DRM d’un fichier chiffré, voir `com.adobe.flashaccess.samples.mediapackager.ExamineContent` dans les outils de ligne de commande de mise en oeuvre de référence [!DNL samples/] répertoire .
