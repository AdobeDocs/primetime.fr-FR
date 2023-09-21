---
title: Préparation des mots de passe pour les fichiers de propriétés du serveur
description: Préparation des mots de passe pour les fichiers de propriétés du serveur
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Préparation des mots de passe pour les fichiers de propriétés du serveur{#prepare-passwords-for-the-server-properties-files}

L’implémentation de référence fournit `ScrambleUtil.class`, une classe qui assure la sécurité du mot de passe de vos informations d’identification.

Utilisez cet outil pour chiffrer le mot de passe avant de l’inclure dans la variable [!DNL flashaccess-refimpl.properties] fichier .

Pour exécuter l’outil, vous pouvez utiliser un script Ant ou Java.

L’utilitaire génère le mot de passe chiffré, que vous devez copier dans la variable [!DNL flashaccess-refimpl.properties] fichier .

>[!NOTE]
>
>Les mots de passe qui ont été codés avec le `ScrambleUtil.class` qui a été fourni avec l’implémentation de référence ne fonctionne pas avec le serveur Primetime DRM pour la diffusion en continu protégée.
