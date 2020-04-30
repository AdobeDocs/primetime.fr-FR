---
seo-title: Utiliser un encodeur tiers
title: Utiliser un encodeur tiers
uuid: 8649303c-b8e6-4c02-a8ad-5734af850bfe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Utiliser un encodeur tiers{#use-a-third-party-encoder}

Certains clients disposent peut-être déjà d’un pipeline de préparation de contenu, utilisant un encodeur vidéo matériel ou logiciel (ou Adobe Media Server). Si tel est le cas, tout produit qui peut actuellement créer du contenu protégé par DRM Primetime peut assembler du contenu pour le DRM de Primetime Cloud en utilisant les mêmes paramètres de configuration que le kit de protection DRM de Primetime Cloud. Les informations requises peuvent être obtenues à partir des fichiers de configuration existants inclus dans le kit : [!DNL config_hls.xml] ou [!DNL config_hds.xml].

Les éléments de configuration pertinents sont les suivants :

* URL du serveur de licences
* URL du serveur de clés
* Certificat du serveur de licences
* Certificat de transport

