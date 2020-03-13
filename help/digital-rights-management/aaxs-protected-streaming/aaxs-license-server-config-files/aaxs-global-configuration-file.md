---
seo-title: Fichier de configuration global
title: Fichier de configuration global
uuid: 10370bc0-36ab-4e43-9e75-c46a7177874c
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Fichier de configuration global{#global-configuration-file}

Le fichier de configuration flashaccess-global.xml contient les paramètres qui s’appliquent à tous les locataires du serveur de licences. Ce fichier doit se trouver dans *LicenseServer.ConfigRoot*. Voir le répertoire configs pour consulter un exemple de fichier de configuration globale. Le fichier de configuration globale comprend les éléments suivants :

* Mise en cache — Contrôle la mise en cache des fichiers de configuration en mémoire. Pour une explication des paramètres de mise en cache, voir &quot;Mise à jour des fichiers de configuration&quot;.
* Journalisation — Indique le niveau de journalisation et la fréquence d’enroulement des fichiers journaux.
* Mot de passe HSM — Obligatoire uniquement si un HSM est utilisé pour stocker les informations d’identification du serveur.

Voir les commentaires dans l&#39;exemple de fichier de configuration globale situé dans `<AdobeAccessDVD>\Adobe Access Server for Protected Streaming\configs` pour plus de détails.
