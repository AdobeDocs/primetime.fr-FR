---
description: 'null'
seo-description: 'null'
seo-title: Configuration logicielle requise
title: Configuration logicielle requise
uuid: 9faa229b-1abf-4b55-b293-247777bcb1db
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Configuration logicielle requise {#software-requirements}

* Tomcat 6
* JDK 1.8

## Diffusion de code / Contenu du package{#code-delivery-package-contents}

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

## Obtention des certificats du serveur d’individualisation{#obtain-individualization-server-certificates}

Pour utiliser le serveur d’individualisation sur site, vous devez d’abord obtenir deux informations d’identification numériques (certificats) :

* *Informations d&#39;identification*  de transport d&#39;individualisation - émises par l&#39;Adobe
* *Informations d&#39;identification*  d&#39;autorité de certification d&#39;individualisation - émises par Symantec (VeriSign)

Pour obtenir ces certificats, envoyez une demande via un ticket Zendesk à : [https://adobeprimetime.zendesk.com](https://adobeprimetime.zendesk.com)

Notez que ces informations d’identification s’ajoutent aux informations d’identification requises pour l’exploitation d’un serveur de licences DRM Primetime.