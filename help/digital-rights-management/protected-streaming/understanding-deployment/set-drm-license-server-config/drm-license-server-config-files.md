---
seo-title: Fichiers de configuration du serveur de licences
title: Fichiers de configuration du serveur de licences
uuid: 7c7e0f76-2ced-45af-9542-99e06ec31cda
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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
