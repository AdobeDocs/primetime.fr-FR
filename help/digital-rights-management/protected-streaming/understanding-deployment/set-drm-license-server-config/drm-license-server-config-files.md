---
title: Fichiers de configuration du serveur de licences
description: Fichiers de configuration du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# Fichiers de configuration du serveur de licences{#license-server-configuration-files}

Le serveur DRM Adobe Primetime pour la diffusion protégée requiert les types de fichiers de configuration suivants :

* Fichier de configuration global ( [!DNL flashaccess-global.xml])
* Fichier de configuration du client pour chaque tenant ( [!DNL flashaccess-tenant.xml])

Après avoir modifié les fichiers de configuration, Adobe vous recommande d’utiliser les utilitaires fournis avec Primetime DRM Server for Protected Streaming pour vérifier que les fichiers sont bien formés.

Voir *Validation de configuration*.

Si vous souhaitez éviter de rendre les mots de passe disponibles en texte clair dans les fichiers de configuration, vous devez chiffrer tous les mots de passe que vous avez spécifiés dans les fichiers de configuration globale et client à l’aide de l’outil Scrambler fourni par Adobe.

Voir *Scrambler de mot de passe* pour plus d’informations sur le chiffrement des mots de passe.
