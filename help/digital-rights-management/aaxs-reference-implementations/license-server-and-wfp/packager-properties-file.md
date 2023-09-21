---
title: Fichier de propriétés du package
description: Fichier de propriétés du package
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Fichier de propriétés du package {#packager-properties-file}

Utilisez la variable [!DNL flashaccess-refimpl-packager.properties] pour configurer le composant Watched Folder Packager de l’implémentation de référence. Veillez à définir au minimum l’URL du serveur de licences, le certificat du serveur de licences, les informations d’identification du package et les options de protection des clés. Ce fichier contient également l’emplacement de chaque dossier de contrôle (packager.watchfolder.source). `n`). Toute modification apportée aux valeurs de ce fichier de propriétés prendra effet la prochaine fois que le module de dossier de contrôle s’exécute (le redémarrage du serveur n’est pas nécessaire). Cependant, en cas d’erreur de configuration dans le programme de configuration, le thread du gestionnaire de dossiers de contrôle se ferme et le serveur doit être redémarré pour redémarrer le thread du gestionnaire de modules.
