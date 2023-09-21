---
title: Diffusion du code / Contenu du package
description: Diffusion du code / Contenu du package
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Diffusion du code / Contenu du package{#code-delivery-package-contents}

Le package Adobe Primetime DRM On Premise Individualization Server contient les éléments suivants :

* [!DNL flashaccess.war] - Le serveur d’individualisation
* [!DNL flashaccess-kgs.war] - Serveur de génération de clés optionnel
* [!DNL /shared] - Contient :

   * [!DNL adobe-flashaccess-certs.jar]
   * [!DNL AdobeInitial.properties] - Exemple de fichier de propriétés

* [!DNL thirdparty/] - Inclut la prise en charge de Crypto-J en tant que bibliothèques natives :

   * [!DNL libjsafe.so] (Linux)
   * [!DNL jsafe.dll] (Windows)

* [!DNL adobe-flashaccess-i15n-setup.jar] - Utilitaire de chiffrement des mots de passe des informations d’identification du serveur
* [!DNL ROOT] - contient une [!DNL crossdomain.xml] fichier

* Fichiers cache de l’IFC - Prétéléchargés
* [!DNL addIndivCert.py] - Script de mise à jour de la racine de confiance d’un serveur de licences pour prendre en charge les individualisations On Premise
* [!DNL CreateMetadata.jar] - Utilitaire de création de métadonnées DRM On Premise
* [!DNL client_sample/] - Dossier contenant un extrait de code client
* Notes de mise à jour - Pour tout ajout de dernière minute à la documentation

