---
description: 'null'
seo-description: 'null'
seo-title: Préparation des mots de passe pour les fichiers de propriétés du serveur
title: Préparation des mots de passe pour les fichiers de propriétés du serveur
uuid: 3e00ba9b-b692-4713-8306-5ab896461f2a
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '103'
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
