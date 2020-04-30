---
seo-title: Fichiers de configuration du serveur de licences
title: Fichiers de configuration du serveur de licences
uuid: 7c7e0f76-2ced-45af-9542-99e06ec31cda
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Fichiers de configuration du serveur de licences{#license-server-configuration-files}

Le serveur DRM d’Adobe Primetime pour la diffusion en flux continu protégé requiert les types de fichiers de configuration suivants :

* Fichier de configuration global ( [!DNL flashaccess-global.xml])
* Fichier de configuration du client pour chaque client ( [!DNL flashaccess-tenant.xml])

Après avoir modifié les fichiers de configuration, Adobe recommande d’utiliser les utilitaires fournis avec le serveur DRM Primetime pour la diffusion en flux continu protégée afin de vérifier que les fichiers sont bien formés.

Voir *Configuration Validator*.

Si vous souhaitez éviter de rendre les mots de passe disponibles en texte clair dans les fichiers de configuration, vous devez chiffrer tous les mots de passe que vous avez spécifiés dans les fichiers de configuration globale et locataire à l’aide de l’outil Scrambler fourni par Adobe.

Voir *Mot de passe Scrambler* pour en savoir plus sur le chiffrement des mots de passe.
