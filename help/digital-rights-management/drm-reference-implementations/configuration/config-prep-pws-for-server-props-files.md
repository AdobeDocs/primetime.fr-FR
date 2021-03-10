---
title: Préparation des mots de passe pour les fichiers de propriétés du serveur
description: Préparation des mots de passe pour les fichiers de propriétés du serveur
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---


# Préparation des mots de passe pour les fichiers de propriétés du serveur{#prepare-passwords-for-the-server-properties-files}

L&#39;implémentation de référence fournit `ScrambleUtil.class`, une classe qui assure la sécurité du mot de passe de vos informations d&#39;identification.

Utilisez cet outil pour chiffrer le mot de passe avant de l&#39;inclure dans le fichier [!DNL flashaccess-refimpl.properties].

Pour exécuter l’outil, vous pouvez utiliser un script Ant ou Java.

L&#39;utilitaire génère le mot de passe chiffré que vous devez copier dans le fichier [!DNL flashaccess-refimpl.properties].

>[!NOTE]
>
>Les mots de passe codés avec le `ScrambleUtil.class` fourni avec l’implémentation de référence ne fonctionnent pas avec le serveur DRM Primetime pour la diffusion en flux continu protégée.
