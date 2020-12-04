---
seo-title: Fichier de propriétés Packager
title: Fichier de propriétés Packager
uuid: 156624ec-66f0-4718-8a66-ed04a47f234d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Fichier de propriétés de package {#packager-properties-file}

Utilisez le fichier [!DNL flashaccess-refimpl-packager.properties] pour configurer le composant Watched Folder Packager de l’implémentation de référence. Au minimum, veillez à définir l’URL du serveur de licences, le certificat du serveur de licences, les informations d’identification du gestionnaire de packages et les options de protection des clés. Ce fichier contient également l’emplacement de chaque dossier de contrôle (packager.watchfolder.source. `n`). Toute modification apportée aux valeurs de ce fichier de propriétés prendra effet lors de la prochaine exécution du gestionnaire de dossiers de contrôle (le redémarrage du serveur n’est pas nécessaire). Cependant, en cas d’erreur de configuration dans le gestionnaire de package, le thread de mise en package du dossier de contrôle se ferme et le serveur doit être redémarré pour redémarrer le thread de mise en package.
