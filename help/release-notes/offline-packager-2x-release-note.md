---
title: Versions de Primetime Offline Packager 2.x
description: Nouveautés des versions 2.1 et 2.3.1 de Primetime Offline Packager
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
translation-type: tm+mt
source-git-commit: b33240bf1b42b80389cd95a7ae4d3f85185a2d32
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---


# Versions de Primetime Offline Packager {#primetime-offline-packager-x-releases}

Nouveautés des versions 2.1 et 2.3.1 de Primetime Offline Packager

## Nouveautés de Primetime Offline Packager 2.3.1 (octobre 2016) {#what-s-new-in-primetime-offline-packager-oct}

La version active le Profil à la demande pour MPEG-DASH, ajoute la prise en charge de l’option `validate` pour l’outil PlaylistCreator et comporte quelques correctifs clés pour les scénarios Multi-DRM répertoriés ci-dessous.

| **Numéro de publication** | **Description** |
|---|---|
| PTPUB-985 | HLS AAXS et Sample-AES ne fonctionnent pas pour la clé générée par le gestionnaire de package. |
| PTPUB-973 | Correction d’une erreur dans l’algorithme de chiffrement pour certains contenus Widevine spécifiques. |
| PTPUB-964 | Le chiffrement CENC est rompu pour certains types de supports sur certains lecteurs - Android TVSDK. |
| PTPUB-954 | Le chiffrement Sample-AES contourne AAXS DRM par défaut / Erreur générée avec la diffusion de clés distantes activée. |
| PTPUB-951 | Le gestionnaire de package hors ligne ne renvoie pas d&#39;exception lorsque key_file_path n&#39;est pas spécifié avec Widevine. Il lance plutôt NPE. |

La documentation la plus récente de Primetime Packagers est disponible à l’adresse [https://help.adobe.com/en_US/primetime/api/packagers/index.html](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

### Problème connu dans la version 2.3.1 {#known-issue-in-version}

Cette version présente les problèmes suivants.

| **Numéro de publication** | **Description** |
|---|---|
| PTPUB-1005 | PlaylistCreator ne fournit pas l’URL correcte pour le fichier .pssh dans le fichier .mpd de dernier niveau généré pour le DRM AAXS. |
| PTPUB-1001 | PlaylistCreator doit renvoyer une erreur lorsque le chemin d’accès vide est fourni via le paramètre in_path. |
| PTPUB-990 | Pour DASH, Offline Packager n’écrit pas de package généré IV sur le disque lorsque les paramètres `log_vi` et `iv_out_path` sont spécifiés. |
| PTPUB-980 | Lorsque le fichier de configuration est utilisé pour le conditionnement, l&#39;utilisation du paramètre `key_url` ne supprime pas les guillemets des entrées fournies. |

## Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager}

### Configuration minimale requise {#minimum-system-requirements}

Systèmes d’exploitation pris en charge

* Linux CentOS 6.3 64 bits

Configuration matérielle requise

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon® double ou plus rapide recommandé)

* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandés)

* Disque dur

(Disk-SAS) : 10 Go minimum avec 7,5 000 tr/min

(Disk-SSD) : Vitesse de lecture/écriture de 400 Mops

(NAS) : 1 Go de lien dédié

Configuration logicielle requise

* Oracle Java SE 1.8 ou version ultérieure

### Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager-1}

1. Téléchargez le logiciel Java SE à partir du [site de l&#39;Oracle](https://www.oracle.com/technetwork/java/javase/downloads/index.html) et suivez les instructions d&#39;installation.
1. Extrayez sur le disque le fichier d&#39;archive Adobe Primetime Offline Packager 2.3.1 nommé `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip`.

### Configuration de Offline Packager 2.3.1 {#configuring-the-offline-packager}

Les instructions de configuration sont disponibles dans le guide de prise en main de Primetime Offline Packager à l’adresse [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

## Nouveautés de Primetime Offline Packager 2.1 (juillet 2015) {#what-s-new-in-primetime-offline-packager-july}

Prise en charge de PlayReady BuyDRM (pour DASH). Pour plus d&#39;informations, consultez la documentation d&#39;aide [disponible ici](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

L’amélioration suivante a également été apportée à l’outil de création de package hors ligne.

PTPUB-780 Prise en charge Ajoutée de la balise EXT-X-DÉBUT

## Nouveautés de Primetime Offline Packager 2.0 (juin 2015) {#what-s-new-in-primetime-offline-packager-june}

La prise en charge de la sortie DASH a été ajoutée. Pour plus d&#39;informations, consultez la documentation du produit [ici](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

Les problèmes suivants ont également été corrigés dans cette version.

* PTPUB-783 Offline Packager peut désormais gérer des fichiers WebVTT vides.
* PTPUB-781 Les artefacts en sortie HLS dans Chrome lorsque certains fichiers MP4 transcodés sont conditionnés avec un packager hors ligne pour produire une sortie MBR.

## Adobe Primetime Offline Packager 2.1 {#adobe-primetime-offline-packager-2}

### Configuration minimale requise {#minimum-system-requirements-1}

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon® double ou plus rapide recommandé)

* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandés)

* Carte Ethernet 1 Gb recommandée (plusieurs cartes réseau et 10 Gb également pris en charge)

* Disque dur

   * (Disk-SAS) : 10 Go minimum avec 7,5 000 tr/min
   * (Disk-SSD) : Vitesse de lecture/écriture de 400 Mops
   * (NAS) : 1 Go de lien dédié

**Configuration logicielle requise**

* Oracle Java SE 1.8 ou version ultérieure

### Installation de Offline Packager 2.1 {#installing-offline-packager}

1. Téléchargez le logiciel Java SE à partir du [site de l&#39;Oracle](https://www.oracle.com/technetwork/java/javase/downloads/index.html) et suivez les instructions d&#39;installation.
1. Extrayez le `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip` sur votre disque.

### Configuration de Offline Packager 2.1 {#configuring-the-offline-packager-1}

Reportez-vous au document de prise en main de Primetime Offline Packager pour obtenir les détails de configuration disponibles ici [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à la [page Apprentissage et support Adobe Primetime](https://helpx.adobe.com/support/primetime.html).