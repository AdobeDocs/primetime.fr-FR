---
title: Configuration logicielle requise
description: Configuration logicielle requise
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Configuration logicielle requise {#software-requirements}

* Tomcat 6
* JDK 1.8

## Diffusion du code / Contenu du package{#code-delivery-package-contents}

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

## Obtention de certificats de serveur d’individualisation{#obtain-individualization-server-certificates}

Pour utiliser le serveur d’individualisation On Premise, vous devez d’abord obtenir deux informations d’identification numériques (certificats) :

* *Informations d’identification de transport d’individualisation* - émis par l’Adobe
* *Informations d’identification de l’autorité de certification de l’individualisation* - émis par Symantec (VeriSign)

Pour obtenir ces certificats, soumettez une demande via un ticket Zendesk à : [https://adobeprimetime.zendesk.com](https://adobeprimetime.zendesk.com)

Notez que ces informations d’identification s’ajoutent aux informations d’identification requises pour l’exploitation d’un serveur de licences DRM Primetime.
