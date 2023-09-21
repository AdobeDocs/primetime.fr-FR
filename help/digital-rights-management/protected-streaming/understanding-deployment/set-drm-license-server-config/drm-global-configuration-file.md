---
description: Le fichier de configuration flashaccess-global.xml comprend les paramètres qui s’appliquent à tous les clients du serveur de licences.
title: Fichier de configuration global
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Fichier de configuration global{#global-configuration-file}

Le fichier de configuration flashaccess-global.xml comprend les paramètres qui s’appliquent à tous les clients du serveur de licences.

Vous devez placer le fichier de configuration dans la variable [!DNL LicenseServer.ConfigRoot] répertoire .

Voir [!DNL configs] pour un exemple de fichier de configuration global.

Le fichier de configuration global comprend :

* Mise en cache : contrôle la mise en cache des fichiers de configuration en mémoire.

  Voir *Mise à jour des fichiers de configuration* pour plus d’informations sur les paramètres de mise en cache.
* Journalisation : indique le niveau de journalisation et la fréquence à laquelle les fichiers journaux sont roulés.
* Mot de passe HSM : requis uniquement si un HSM est utilisé pour stocker les informations d’identification du serveur.

Voir les commentaires dans l’exemple de fichier de configuration global situé dans Primetime DRM `<DVD>`\Adobe Primetime DRM Server for Protected Streaming\configs pour plus d’informations.
