---
title: Utiliser un encodeur tiers
description: Utiliser un encodeur tiers
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Utiliser un encodeur tiers{#use-a-third-party-encoder}

Certains clients disposent peut-être déjà d’un pipeline de préparation de contenu, utilisant un encodeur vidéo matériel ou logiciel (ou Adobes Medium Server). Si tel est le cas, tout produit qui peut actuellement créer du contenu protégé par DRM Primetime peut assembler du contenu pour le DRM de Primetime Cloud en utilisant les mêmes paramètres de configuration que le kit de protection DRM de Primetime Cloud. Les informations requises peuvent être obtenues à partir des fichiers de configuration existants inclus dans le kit : [!DNL config_hls.xml] ou [!DNL config_hds.xml].

Les éléments de configuration pertinents sont les suivants :

* URL du serveur de licences
* URL du serveur de clés
* Certificat du serveur de licences
* Certificat de transport

