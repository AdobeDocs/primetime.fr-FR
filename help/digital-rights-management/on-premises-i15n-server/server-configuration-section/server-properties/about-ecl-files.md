---
title: À propos des fichiers C
description: À propos des fichiers C
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# À propos des fichiers C{#about-eci-files}

Outre les listes CRL, vous devez également mettre à jour régulièrement les fichiers d’interface commune incorporée (CID). Chaque fois qu’Adobe ajoute la prise en charge d’une nouvelle plateforme cliente DRM Primetime (par exemple : iOS, Android, Windows FlashPlayer, etc.), un nouvel enregistrement CID est créé. Afin de soutenir l’individualisation de ce client, un enregistrement ICE correspondant doit être présent sur le serveur d’individualisation.

Comme la publication de nouveaux clients DRM Primetime n’est pas très fréquente, Adobe publiera des données d’ICE mises à jour en fonction des besoins. Régulièrement, Adobe collectera les fichiers ICE et les hébergera à l’emplacement ci-dessous pour distribution :

```
http://cdmdownload.adobe.com/indiv/onprem/eci/Latest.txt
```

La variable [!DNL Latest.txt] contient l’URL du fichier de distribution CRL le plus récent.

Adobe va créer le fichier zip d’ICE de la manière décrite ci-dessous :

Structure de dossier :

```
ECI\*
```

Le contenu du dossier est compressé de manière récursive :

```
zip -R ECI ECI.zip
```

Un condensé OpenSSL SHA-256 sera calculé à partir du fichier zip :

```
openssl dgst -sha256 -hex ECI.zip
```

Le fichier zip sera renommé pour contenir la date d’archivage ainsi que le résumé SHA-256 :

```
Rename ECI.zip to <DATE_SHA-256>.zip
```

Par exemple :

```
20150310_aea45bf06241f04fba2b310ff9a8066c6aba73c8d22387b60509481e9cefc43e.zip
```

Vérifiez régulièrement l’emplacement ci-dessus pour les fichiers ICE mis à jour.

Procédez comme suit pour l’installation après téléchargement :

1. Notez le condensé SHA-256 et recalculez-le à l’aide d’OpenSSL ou d’un outil équivalent.
1. Comparez-la à celle spécifiée dans le nom de fichier.
1. Renommez le fichier en [!DNL ECI.zip].
1. Décompressez le fichier [!DNL ECI] répertoire .
1. Remplacez l’ancien répertoire d’ICE par le nouveau.
1. Redémarrez le serveur d’individualisation.
