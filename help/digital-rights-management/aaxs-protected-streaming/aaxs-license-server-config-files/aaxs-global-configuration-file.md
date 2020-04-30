---
seo-title: Fichier de configuration global
title: Fichier de configuration global
uuid: 10370bc0-36ab-4e43-9e75-c46a7177874c
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Fichier de configuration global{#global-configuration-file}

Le fichier de configuration flashaccess-global.xml contient des paramètres qui s’appliquent à tous les locataires du serveur de licences. Ce fichier doit se trouver dans *LicenseServer.ConfigRoot*. Consultez le répertoire configs pour un exemple de fichier de configuration global. Le fichier de configuration global comprend les éléments suivants :

* Mise en cache : contrôle la mise en cache des fichiers de configuration en mémoire. Pour une explication des paramètres de mise en cache, voir Mise à jour des fichiers de configuration.
* Journalisation : indique le niveau de journalisation et la fréquence d&#39;enregistrement des fichiers journaux.
* Mot de passe HSM : requis uniquement si un HSM est utilisé pour stocker les informations d&#39;identification du serveur.

Consultez les commentaires de l&#39;exemple de fichier de configuration globale situé dans `<AdobeAccessDVD>\Adobe Access Server for Protected Streaming\configs` pour plus de détails.
