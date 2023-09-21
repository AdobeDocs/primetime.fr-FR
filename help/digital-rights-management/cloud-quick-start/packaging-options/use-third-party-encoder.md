---
title: Utilisation d’un encodeur tiers
description: Utilisation d’un encodeur tiers
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Utilisation d’un encodeur tiers{#use-a-third-party-encoder}

Certains clients peuvent déjà avoir mis en place un pipeline de préparation de contenu, à l’aide d’un encodeur vidéo matériel ou logiciel (ou Adobe Media Server). Si c’est le cas, tout produit qui peut actuellement créer du contenu protégé par DRM Primetime peut compresser le contenu pour DRM Primetime Cloud en utilisant les mêmes paramètres de configuration que le kit de protection DRM Primetime Cloud. Les informations requises peuvent être obtenues à partir de l’un des fichiers de configuration existants inclus dans le kit : [!DNL config_hls.xml] ou [!DNL config_hds.xml].

Les éléments de configuration pertinents sont les suivants :

* URL du serveur de licences
* URL du serveur clé
* Certificat du serveur de licences
* Certificat de transport
