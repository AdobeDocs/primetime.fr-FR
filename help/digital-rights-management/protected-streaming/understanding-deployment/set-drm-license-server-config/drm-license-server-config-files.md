---
title: Fichiers de configuration du serveur de licences
description: Fichiers de configuration du serveur de licences
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Fichiers de configuration du serveur de licences{#license-server-configuration-files}

Le serveur Adobe Primetime DRM Server pour la diffusion en flux continu protégée requiert les types de fichiers de configuration suivants :

* Fichier de configuration global ( [!DNL flashaccess-global.xml])
* Fichier de configuration du client pour chaque client ( [!DNL flashaccess-tenant.xml])

Une fois les fichiers de configuration modifiés, l’Adobe vous recommande d’utiliser les utilitaires fournis avec le serveur DRM Primetime pour la diffusion en flux continu protégée afin de vérifier que les fichiers sont bien formés.

Voir *Validation de configuration*.

Si vous souhaitez éviter de rendre les mots de passe disponibles en texte clair dans les fichiers de configuration, vous devez chiffrer tous les mots de passe que vous avez spécifiés dans les fichiers de configuration globale et locataire en utilisant l&#39;outil Scrambler fourni par l&#39;Adobe.

Voir *Mot de passe Scrambler* pour plus d’informations sur le chiffrement des mots de passe.
