---
title: Fichier de configuration global
description: Fichier de configuration global
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# Fichier de configuration global{#global-configuration-file}

Le fichier de configuration flashaccess-global.xml contient les paramètres qui s’appliquent à tous les clients du serveur de licences. Ce fichier doit se trouver dans *LicenseServer.ConfigRoot*. Voir le répertoire configs pour obtenir un exemple de fichier de configuration global. Le fichier de configuration global comprend les éléments suivants :

* Mise en cache : contrôle la mise en cache des fichiers de configuration en mémoire. Pour une explication des paramètres de mise en cache, voir &quot;Mise à jour des fichiers de configuration&quot;.
* Journalisation : indique le niveau de journalisation et la fréquence à laquelle les fichiers journaux sont roulés.
* Mot de passe HSM : requis uniquement si un HSM est utilisé pour stocker les informations d’identification du serveur.

Consultez les commentaires dans l’exemple de fichier de configuration global situé dans `<AdobeAccessDVD>\Adobe Access Server for Protected Streaming\configs` pour plus d’informations.
