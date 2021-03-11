---
title: Fichier de propriétés Packager
description: Fichier de propriétés Packager
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Fichier de propriétés de package {#packager-properties-file}

Utilisez le fichier [!DNL flashaccess-refimpl-packager.properties] pour configurer le composant Watched Folder Packager de l’implémentation de référence. Au minimum, veillez à définir l’URL du serveur de licences, le certificat du serveur de licences, les informations d’identification du gestionnaire de packages et les options de protection des clés. Ce fichier contient également l’emplacement de chaque dossier de contrôle (packager.watchfolder.source. `n`). Toute modification apportée aux valeurs de ce fichier de propriétés prendra effet lors de la prochaine exécution du gestionnaire de dossiers de contrôle (le redémarrage du serveur n’est pas nécessaire). Cependant, en cas d’erreur de configuration dans le gestionnaire de package, le thread de mise en package du dossier de contrôle se ferme et le serveur doit être redémarré pour redémarrer le thread de mise en package.
