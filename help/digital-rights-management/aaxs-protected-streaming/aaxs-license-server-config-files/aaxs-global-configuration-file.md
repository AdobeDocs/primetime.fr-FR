---
title: Fichier de configuration global
description: Fichier de configuration global
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Fichier de configuration global{#global-configuration-file}

Le fichier de configuration flashaccess-global.xml contient des paramètres qui s’appliquent à tous les locataires du serveur de licences. Ce fichier doit se trouver dans *LicenseServer.ConfigRoot*. Consultez le répertoire configs pour un exemple de fichier de configuration global. Le fichier de configuration global comprend les éléments suivants :

* Mise en cache : contrôle la mise en cache des fichiers de configuration en mémoire. Pour une explication des paramètres de mise en cache, voir Mise à jour des fichiers de configuration.
* Journalisation : indique le niveau de journalisation et la fréquence d&#39;enregistrement des fichiers journaux.
* Mot de passe HSM : requis uniquement si un HSM est utilisé pour stocker les informations d&#39;identification du serveur.

Pour plus d&#39;informations, consultez les commentaires de l&#39;exemple de fichier de configuration globale situé dans `<AdobeAccessDVD>\Adobe Access Server for Protected Streaming\configs`.
