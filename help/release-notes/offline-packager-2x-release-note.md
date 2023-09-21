---
title: Versions de Primetime Offline Packager 2.x
description: Nouveautés des versions 2.1 et 2.3.1 de Primetime Offline Packager
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Versions de Primetime Offline Packager {#primetime-offline-packager-x-releases}

Nouveautés des versions 2.1 et 2.3.1 de Primetime Offline Packager

## Nouveautés de Primetime Offline Packager 2.3.1 (octobre 2016)  {#what-s-new-in-primetime-offline-packager-oct}

La version active le profil On-demand pour MPEG-DASH, ajoute la prise en charge de la fonction `validate` pour l’outil PlaylistCreator et comporte quelques correctifs clés pour les scénarios multi-DRM répertoriés ci-dessous.

| **Numéro de problème** | **Description** |
|---|---|
| PTPUB-985 | HLS AAXS et Sample-AES ne fonctionnent pas pour la clé générée par packager |
| PTPUB-973 | Correction d’une erreur dans l’algorithme de chiffrement pour certains contenus Widevine spécifiques. |
| PTPUB-964 | Cryptage CENC rompu pour certains types de médias sur certains lecteurs - Android TVSDK. |
| PTPUB-954 | Le cryptage Sample-AES contourne AAXS DRM par défaut / Erreur générée avec la diffusion de clé distante activée. |
| PTPUB-951 | Le package hors ligne ne renvoie pas d’exception lorsque key_file_path n’est pas spécifié avec Windows. Il renvoie NPE à la place. |

La documentation la plus récente sur les modules Primetime est disponible à l’adresse [https://help.adobe.com/en_US/primetime/api/packagers/index.html](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

### Problème connu dans la version 2.3.1 {#known-issue-in-version}

Cette version présente les problèmes suivants.

| **Numéro de problème** | **Description** |
|---|---|
| PTPUB-1005 | PlaylistCreator ne fournit pas l’URL correcte pour le fichier .pssh dans le fichier .mpd de niveau défini final généré pour le DRM AAXS. |
| PTPUB-1001 | PlaylistCreator doit générer une erreur lorsque le chemin vide est fourni via le paramètre in_path . |
| PTPUB-990 | Pour DASH, Offline Packager n’écrit pas de module généré IV sur le disque lorsque les paramètres `log_vi` &amp; `iv_out_path` sont spécifiées. |
| PTPUB-980 | Lorsque le fichier de configuration est utilisé pour le conditionnement, en utilisant le paramètre `key_url` ne supprime pas les guillemets des entrées fournies. |

## Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager}

### Configuration minimale requise {#minimum-system-requirements}

Systèmes d’exploitation pris en charge

* Linux CentOS 6.3 64 bits

Configuration matérielle requise

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon double ® ou plus rapide recommandé)

* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandé)

* Disque dur

(Disk-SAS) : 10 Go minimum avec 7,5 K tr/min

(Disque-SSD) : vitesse de lecture/écriture de 400 Mbit/s

(NAS) : lien dédié 1 Go

Exigences logicielles

* Oracle Java SE 1.8 ou version ultérieure

### Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager-1}

1. Téléchargez le logiciel Java SE à partir du [Oracle site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) et suivez les instructions d’installation.
1. Extrayez le fichier d’archive Adobe Primetime Offline Packager 2.3.1 nommé `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip` sur le disque.

### Configuration de l’outil Hors ligne Packager 2.3.1 {#configuring-the-offline-packager}

Les instructions de configuration sont disponibles dans le guide de démarrage de Primetime Offline Packager à l’adresse [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Nouveautés de Primetime Offline Packager 2.1 (juillet 2015) {#what-s-new-in-primetime-offline-packager-july}

Prise en charge de PlayReady BuyDRM (pour DASH). Pour plus d’informations, reportez-vous à la documentation d’aide . [disponible ici](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

L’amélioration suivante a également été apportée au module hors ligne.

PTPUB-780 Prise en charge supplémentaire de la balise EXT-X-START

## Nouveautés de Primetime Offline Packager 2.0 (juin 2015) {#what-s-new-in-primetime-offline-packager-june}

Ajout de la prise en charge de la sortie DASH. Consultez la documentation du produit [here](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html) pour plus d’informations.

Les problèmes suivants ont également été corrigés dans cette version.

* PTPUB-783 Offline Packager peut désormais gérer des fichiers WebVTT vides.
* PTPUB-781 Les artefacts en sortie HLS sur Chrome lorsque certaines ressources MP4 transcodées sont incluses dans un module hors ligne pour produire une sortie MBR.

## Adobe Primetime Offline Packager 2.1 {#adobe-primetime-offline-packager-2}

### Configuration minimale requise {#minimum-system-requirements-1}

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon double ® ou plus rapide recommandé)

* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandé)

* Carte Ethernet 1 Go recommandée (plusieurs cartes réseau et 10 Go également pris en charge)

* Disque dur

   * (Disk-SAS) : 10 Go minimum avec 7,5 K tr/min
   * (Disque-SSD) : vitesse de lecture/écriture de 400 Mbit/s
   * (NAS) : lien dédié 1 Go

**Exigences logicielles**

* Oracle Java SE 1.8 ou version ultérieure

### Installation de Offline Packager 2.1 {#installing-offline-packager}

1. Téléchargez le logiciel Java SE à partir du [Oracle site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) et suivez les instructions d’installation.
1. Extrayez le `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip`, sur votre disque.

### Configuration de Offline Packager 2.1 {#configuring-the-offline-packager-1}

Consultez le document Prise en main de Primetime Offline Packager pour obtenir les détails de configuration disponibles ici. [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://helpx.adobe.com/support/primetime.html) page.
