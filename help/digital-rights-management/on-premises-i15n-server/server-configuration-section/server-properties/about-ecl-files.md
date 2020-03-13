---
seo-title: A propos des fichiers ECI
title: A propos des fichiers ECI
uuid: 124d8ab1-933b-4a1b-992a-919f3d799460
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4

---


# A propos des fichiers ECI{#about-eci-files}

Outre les listes CRL, vous devez également mettre à jour régulièrement les fichiers ECI (Embedded Common Interface). Chaque fois qu’Adobe ajoute la prise en charge d’une nouvelle plateforme client DRM Primetime (par exemple : iOS, Android, Windows Flash Player, etc.), un nouvel enregistrement ECI est créé. Afin de soutenir l’individualisation de ce client, un enregistrement ECI correspondant doit être présent sur le serveur d’individualisation.

Comme la publication de nouveaux clients DRM Primetime n’est pas très fréquente, Adobe publiera des données ECI mises à jour en fonction des besoins. Adobe collecte régulièrement des fichiers ECI et les héberge à l’emplacement ci-dessous pour distribution :

```
http://cdmdownload.adobe.com/indiv/onprem/eci/Latest.txt
```

Le [!DNL Latest.txt] fichier contient l’URL du fichier de distribution CRL le plus récent.

Adobe va créer le fichier zip ECI de la manière suivante :

Structure du dossier :

```
ECI\*
```

Le contenu du dossier sera compressé de manière récursive :

```
zip -R ECI ECI.zip
```

Un résumé SHA-256 OpenSSL sera calculé à partir du fichier zip :

```
openssl dgst -sha256 -hex ECI.zip
```

Le fichier zip sera renommé pour contenir la date d’archivage ainsi que le résumé SHA-256 :

```
Rename ECI.zip to <DATE_SHA-256>.zip
```

Par exemple :

```
20150310_aea45bf06241f04fba2b310ff9a8066c6aba73c8d22387b60509481e9cefc43e.zip
```

Vérifiez régulièrement l&#39;emplacement ci-dessus pour les fichiers ECI mis à jour.

Procédez comme suit pour l’installation après le téléchargement :

1. Notez le résumé SHA-256 et recalculez-le à l’aide d’OpenSSL ou d’un outil équivalent.
1. Comparez-le à celui spécifié dans le nom de fichier.
1. Renommez le fichier en [!DNL ECI.zip].
1. Décompressez le [!DNL ECI] répertoire.
1. Remplacez l’ancien répertoire ECI par le nouveau.
1. Redémarrez le serveur d’individualisation.

