---
title: Versions de Primetime Offline Packager 2.x
seo-title: Versions de Primetime Offline Packager 2.x
description: Nouveautés des versions 2.1 et 2.3.1 de Primetime Offline Packager
seo-description: Nouveautés des versions 2.1 et 2.3.1 de Primetime Offline Packager
uuid: 01926a10-890d-477d-b832-e22847d957e0
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 933a0711-846a-4bb7-bf51-b300822a93d4
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Versions de Primetime Offline Packager {#primetime-offline-packager-x-releases}

Nouveautés des versions 2.1 et 2.3.1 de Primetime Offline Packager

## Nouveautés de Primetime Offline Packager 2.3.1 (octobre 2016) {#what-s-new-in-primetime-offline-packager-oct}

La version active les  à la demande pour MPEG-DASH, ajoute la prise en charge de l’ `validate` option pour l’outil PlaylistCreator et comporte quelques correctifs clés pour les scénarios multi-DRM répertoriés ci-dessous.

| **Numéro de publication** | **Description** |
|---|---|
| PTPUB-985 | HLS AAXS et Sample-AES ne fonctionnent pas pour la clé générée par le gestionnaire de package |
| PTPUB-973 | Correction d’une erreur dans l’algorithme de chiffrement pour certains contenus Widevine spécifiques. |
| PTPUB-964 | Chiffrement CENC rompu pour certains types de supports sur certains lecteurs - Android TVSDK. |
| PTPUB-954 | Le chiffrement Sample-AES contourne AAXS DRM par défaut / Erreur générée avec l&#39;activation du de clés distantes. |
| PTPUB-951 | Le gestionnaire de package hors ligne ne renvoie pas d’exception lorsque key_file_path n’est pas spécifié avec Windows. Il lance NPE à la place. |

La dernière documentation de Primetime Packagers est disponible à l’adresse [https://help.adobe.com/en_US/primetime/api/packagers/index.html](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

### Problème connu dans la version 2.3.1 {#known-issue-in-version}

Les problèmes suivants se trouvent dans cette version.

| **Numéro de publication** | **Description** |
|---|---|
| PTPUB-1005 | PlaylistCreator ne fournit pas l’URL correcte pour le fichier .pssh dans le fichier .mpd de dernier niveau généré pour le DRM AAXS. |
| PTPUB-1001 | PlaylistCreator doit renvoyer une erreur lorsque le chemin d’accès vide est fourni via le paramètre in_path. |
| PTPUB-990 | Pour DASH, Hors ligne Packager n’écrit pas le gestionnaire de package généré IV sur le disque lorsque les paramètres `log_vi` &amp; `iv_out_path` sont spécifiés. |
| PTPUB-980 | Lorsque le fichier de configuration est utilisé pour le conditionnement, l’utilisation du paramètre `key_url` ne supprime pas les guillemets des entrées fournies. |

## Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager}

### Configuration minimale requise {#minimum-system-requirements}

Systèmes d’exploitation pris en charge

* Linux CentOS 6.3 64 bits

Configuration matérielle requise

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon® double ou plus rapide recommandé)

* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandés)

* Disque dur

(Disk-SAS): 10 Go minimum avec 7,5 000 tr/min

(Disk-SSD): Vitesse de lecture/écriture de 400 Mops

(NAS) : Lien dédié 1 Go

Configuration logicielle requise

* Oracle Java SE 1.8 ou version ultérieure

### Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager-1}

1. Téléchargez le logiciel Java SE à partir du site [](https://www.oracle.com/technetwork/java/javase/downloads/index.html) Oracle et suivez les instructions d&#39;installation.
1. Extrayez le fichier d’archive Adobe Primetime Offline Packager 2.3.1 nommé `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip` sur le disque.

### Configuration de Offline Packager 2.3.1 {#configuring-the-offline-packager}

Les instructions de configuration sont disponibles dans le guide de prise en main de Primetime Offline Packager à l’adresse [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html.](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Nouveautés de Primetime Offline Packager 2.1 (juillet 2015) {#what-s-new-in-primetime-offline-packager-july}

Prise en charge de PlayReady BuyDRM (pour DASH). Pour plus d&#39;informations, reportez-vous à la documentation d&#39;aide [disponible ici](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

L’amélioration suivante a également été apportée au gestionnaire de package hors ligne.

PTPUB-780 Ajout de la prise en charge de la balise  EXT-X-

## Nouveautés de Primetime Offline Packager 2.0 (juin 2015) {#what-s-new-in-primetime-offline-packager-june}

La prise en charge de la sortie DASH a été ajoutée. Consultez la documentation du produit [ici](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html) pour plus de détails.

Les problèmes suivants ont également été corrigés dans cette version.

* PTPUB-783 Offline Packager peut désormais gérer des fichiers WebVTT vides.
* PTPUB-781 Artefacts dans la sortie HLS sur Chrome lorsque certains fichiers MP4 transcodés sont compressés avec un gestionnaire de package hors ligne pour produire une sortie MBR.

## Adobe Primetime Offline Packager 2.1 {#adobe-primetime-offline-packager-2}

### Configuration minimale requise {#minimum-system-requirements-1}

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon® double ou plus rapide recommandé)

* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandés)

* Carte Ethernet 1 Go recommandée (plusieurs cartes réseau et 10 Go également pris en charge)

* Disque dur

   * (Disk-SAS): 10 Go minimum avec 7,5 000 tr/min
   * (Disk-SSD): Vitesse de lecture/écriture de 400 Mops
   * (NAS) : Lien dédié 1 Go

**Configuration logicielle requise**

* Oracle Java SE 1.8 ou version ultérieure

### Installation de Offline Packager 2.1 {#installing-offline-packager}

1. Téléchargez le logiciel Java SE à partir du site [](https://www.oracle.com/technetwork/java/javase/downloads/index.html) Oracle et suivez les instructions d&#39;installation.
1. Extrayez le `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip`, sur votre disque.

### Configuration de Offline Packager 2.1 {#configuring-the-offline-packager-1}

Reportez-vous au  de prise en main de Primetime Offline Packager pour obtenir les détails de configuration disponibles ici [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Ressources utiles {#helpful-resources}

* Reportez-vous à la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.