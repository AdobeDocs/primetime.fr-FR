---
description: Le fichier de configuration flashaccess-global.xml comprend des paramètres qui s’appliquent à tous les locataires du serveur de licences.
seo-description: Le fichier de configuration flashaccess-global.xml comprend des paramètres qui s’appliquent à tous les locataires du serveur de licences.
seo-title: Fichier de configuration global
title: Fichier de configuration global
uuid: 294d6cff-be07-4b4b-8aa6-943044a1c56f
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Fichier de configuration global{#global-configuration-file}

Le fichier de configuration flashaccess-global.xml comprend des paramètres qui s’appliquent à tous les locataires du serveur de licences.

Vous devez placer le fichier de configuration dans le répertoire [!DNL LicenseServer.ConfigRoot].

Consultez le répertoire [!DNL configs] pour obtenir un exemple de fichier de configuration global.

Le fichier de configuration global comprend :

* Mise en cache : contrôle la mise en cache des fichiers de configuration en mémoire.

   Voir *Mise à jour des fichiers de configuration* pour plus d’informations sur les paramètres de mise en cache.
* Journalisation : indique le niveau de journalisation et la fréquence d&#39;enregistrement des fichiers journaux.
* Mot de passe HSM : requis uniquement si un HSM est utilisé pour stocker les informations d&#39;identification du serveur.

Pour plus d&#39;informations, consultez les commentaires de l&#39;exemple de fichier de configuration globale situé dans le DRM Primetime `<DVD>`\Adobe Primetime DRM Server for Protected Streaming\configs.
