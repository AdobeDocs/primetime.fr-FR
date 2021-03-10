---
title: A propos des fichiers ECI
description: A propos des fichiers ECI
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# A propos des fichiers ECI{#about-eci-files}

Outre les listes CRL, vous devez également régulièrement mettre à jour les fichiers ECI (Embedded Common Interface). Chaque fois que l&#39;Adobe ajoute la prise en charge d&#39;une nouvelle plateforme client DRM Primetime (par exemple : iOS, Android, Windows FlashPlayer, etc.), un nouvel enregistrement ECI est créé. Afin de soutenir l&#39;individualisation de ce client, un enregistrement ECI correspondant doit être présent sur le serveur d&#39;individualisation.

Étant donné que la publication de nouveaux clients DRM Primetime n&#39;est pas très fréquente, l&#39;Adobe publiera des données d&#39;ECI mises à jour au besoin. Régulièrement, l&#39;Adobe recueille les fichiers de l&#39;IFPC et les héberge à l&#39;emplacement ci-dessous pour distribution :

```
http://cdmdownload.adobe.com/indiv/onprem/eci/Latest.txt
```

Le fichier [!DNL Latest.txt] contient l&#39;URL du fichier de distribution CRL le plus récent.

L&#39;Adobe va créer le fichier zip ECI de la manière décrite ci-dessous :

Structure du dossier :

```
ECI\*
```

Le contenu du dossier sera compressé de manière récursive :

```
zip -R ECI ECI.zip
```

Un résumé SHA-256 OpenSSL est calculé à partir du fichier zip :

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

Vous devez vérifier régulièrement l&#39;emplacement ci-dessus pour les fichiers ECI mis à jour.

Procédez comme suit pour l’installation après le téléchargement :

1. Notez le résumé SHA-256 et recalculez-le à l’aide d’OpenSSL ou d’un outil équivalent.
1. Comparez-la à celle spécifiée dans le nom de fichier.
1. Renommez le fichier en [!DNL ECI.zip].
1. Décompressez le répertoire [!DNL ECI].
1. Remplacez l&#39;ancien répertoire ECI par le nouveau.
1. Redémarrez le serveur d’individualisation.

