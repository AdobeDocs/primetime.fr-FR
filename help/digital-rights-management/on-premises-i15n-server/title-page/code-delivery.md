---
title: Diffusion de code / Contenu du package
description: Diffusion de code / Contenu du package
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Diffusion de code / Contenu du package{#code-delivery-package-contents}

Le package Adobe Primetime DRM On Premises Individualization Server contient les éléments suivants :

* [!DNL flashaccess.war] - Le serveur d&#39;individualisation
* [!DNL flashaccess-kgs.war] - Serveur de génération de clés en option
* [!DNL /shared] - Contient :

   * [!DNL adobe-flashaccess-certs.jar]
   * [!DNL AdobeInitial.properties] - Exemple de fichier de propriétés

* [!DNL thirdparty/] - Inclut la prise en charge de Crypto-J en tant que bibliothèques natives :

   * [!DNL libjsafe.so] (Linux)
   * [!DNL jsafe.dll] (Windows)

* [!DNL adobe-flashaccess-i15n-setup.jar] - Utilitaire de chiffrement des mots de passe d&#39;identification du serveur
* [!DNL ROOT] - contient un  [!DNL crossdomain.xml] fichier

* Fichiers cache ECI - Prétéléchargés
* [!DNL addIndivCert.py] - Script de mise à jour de la racine de confiance d&#39;un serveur de licences pour la prise en charge des individualisations sur site
* [!DNL CreateMetadata.jar] - Utilitaire de création de métadonnées DRM sur site
* [!DNL client_sample/] - Un dossier avec un extrait de code client
* Notes de mise à jour - Pour tout ajout de dernière minute à la documentation

