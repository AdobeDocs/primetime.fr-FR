---
description: 'null'
seo-description: 'null'
seo-title: Préparation des mots de passe pour les fichiers de propriétés du serveur
title: Préparation des mots de passe pour les fichiers de propriétés du serveur
uuid: 3e00ba9b-b692-4713-8306-5ab896461f2a
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Préparation des mots de passe pour les fichiers de propriétés du serveur{#prepare-passwords-for-the-server-properties-files}

L’implémentation des références fournit `ScrambleUtil.class`, une classe qui assure la sécurité du mot de passe de vos informations d’identification.

Utilisez cet outil pour chiffrer le mot de passe avant de l’inclure dans le [!DNL flashaccess-refimpl.properties] fichier.

Pour exécuter l’outil, vous pouvez utiliser un script Ant ou Java.

L’utilitaire génère le mot de passe chiffré que vous devez copier dans le [!DNL flashaccess-refimpl.properties] fichier.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Les mots de passe qui ont été codés avec le code `ScrambleUtil.class` fourni avec l’implémentation de référence ne fonctionnent pas avec le serveur DRM Primetime pour la diffusion en flux continu protégée.
