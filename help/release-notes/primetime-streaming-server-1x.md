---
title: Versions de Primetime Streaming Server
seo-title: Versions de Primetime Streaming Server 1.x
description: Nouveautés des versions 1.3 et 1.4 de Primetime Streaming Server.
seo-description: Nouveautés des versions 1.3 et 1.4 de Primetime Streaming Server.
uuid: be05db6b-713f-4406-940d-9f3a805f967b
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: baec714e-9d41-4e8b-b134-13a736885cbd
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1929'
ht-degree: 0%

---


# Versions de Primetime Streaming Server {#primetime-streaming-server-x-releases}

Nouveautés des versions 1.3 et 1.4 de Primetime Streaming Server.

## Nouveautés de Primetime Streaming Server 1.4 (version de décembre) {#what-s-new-in-primetime-streaming-server-december-release}

**Packager hors ligne**

* Les flux Output HLS contiennent désormais des métadonnées ID3 présentes dans MPEG-2 TS
* Les flux audio HLS uniquement peuvent désormais avoir une image statique associée
* Prise en charge de la prise en charge de IV en tant qu’entrée utilisateur pour les workflows de chiffrement AES HLS
* Prise en charge de la sortie IV vers un fichier lorsque IV est généré par le gestionnaire de package hors ligne
* Playlist Creator prend désormais en charge l’association de groupes audio multilingues et de groupes de sous-titres WebVTT multilingues aux flux de médias.

**Origine Server**

* Le chiffrement AES HLS est disponible pour les workflows en direct et VOD. L’Origine Primetime peut appliquer le chiffrement HLS AES à des flux HLS entrants ou à des fichiers MP4.
* Il peut également appliquer le chiffrement JIT HLS AES lorsqu’il est utilisé pour convertir des flux HDS entrants en flux HLS.
* L&#39;Origine Primetime prend désormais en charge les fichiers SWF permettant l&#39;inscription des flux PHLS. Auparavant, il était pris en charge uniquement pour les flux de SPHD.

**Primetime Live Packager**

* Prise en charge de la génération de flux HLS AES-128 pour les flux RTMP et MPEG-2 TS d&#39;entrée

Les certificats PHDS/PHLS ont été actualisés. La même date d&#39;expiration est fixée au 01/10/2016.

### **Correctifs inclus dans la version 1.4** {#bug-fixes-included-in-release}

* PTPUB-282- Le manifeste de niveau fixe HLS créé par OfflinePackager 1.3.1 ne contient pas d&#39;informations de codec et de résolution.
* PTPUB-353 - PlayListCreator ne prend pas en charge l’ajout d’informations WebVTT dans le manifeste de niveau défini.
* PTPUB-583 - L’outil PlaylistCreator effectue un préfixe inattendu sur les URI de groupe avec.
* PTPUB-605 Playlist Creator ne répertoriant pas le groupe SUBTITLE dans chaque flux de variante
* PTPUB-634 - Offline Packager ajoute SpliceInsert au manifeste.
* PTPUB-635- Plusieurs balises SpliceOut insérées pour une seule annonce publicitaire.

### Problème connu dans la version 1.4 {#known-issue-in-release}

* PTPUB- 645 Le mode Imple est imposé même lorsque le mode DPIScte35 est spécifié lorsque les signaux de ligne de commande et les signaux in-stream sont tous deux fournis dans la configuration du gestionnaire de package hors ligne.

## Nouveautés de la version 1.3.1 de Primetime Streaming Server (MAY Release) {#what-s-new-in-primetime-streaming-server-may-release}

La version 1.3.1 fait référence au correctif logiciel. Les améliorations suivantes en font une mise à niveau recommandée pour les clients, car elle consiste en des améliorations de performances clés pour les cas d’utilisation du format JIT MP4 :

1. Correctif de performances pour la génération MP4 JIT m3u8 sur Origine avec DRM, y compris la rotation de clé
1. Ajouté une configuration &quot;CopyQueryParamToJITFragmentURIs&quot; pour copier les paramètres de requête de la demande de manifeste JIT vers les URI de fragment générés pour la conversion JIT MP4. Reportez-vous à la documentation du serveur d’Origines HTTP pour obtenir des exemples d’utilisation.
1. Autoriser les fichiers MP4 sans extension pour la conversion JIT, via la configuration Config/MP4Only ajoutée au fichier vod.xml

### Correctifs inclus dans la version 1.3.1 {#bug-fixes-included-in-release-1}

* 3759167 - Tous les indices SCTE35 ne parviennent pas au manifeste de sortie en raison d’une anomalie d’horodatage survenant lors de l’empaquetage. Appliquez pts_ajustement sur SpliceTime dans TimeSignal de SpliceInfoSection dans le message SCTE35.

### Problèmes connus dans la version 1.3.1 {#known-issues-in-release}

* 3717039 - Lorsque l’outil d’empaquetage est configuré pour produire des indices de mode simple ppp, il doit vraiment rechercher des types de signaux spécifiques, tels que des insertions ou des opportunités de placement, et convertir uniquement ceux-ci en signaux de mode simple. Il doit ignorer d&#39;autres types de signaux tels que le début de programme, le début réseau, etc.

* 3718598 - Lorsque Origine Server est configuré pour diffuser des contenus protégés avec l’accès HSM activé par le client LunaSA principal communique fréquemment avec le module HSM

## Nouveautés de Primetime Streaming Server 1.3 (version d’avril) {#what-s-new-in-primetime-streaming-server-april-release}

La version 1.3 de Primetime apporte plusieurs nouvelles fonctionnalités liées à la diffusion en flux continu de contenu, à une meilleure convivialité et à une meilleure sécurité.

**Serveur de flux continu Primetime en tant que forme unifiée de Live Packager et de serveur d’Origines**

Primetime Live Packager et l’Origine Primetime sont regroupés pour fonctionner comme un seul composant. Ce composant peut être utilisé comme Packager ou comme Origine ou utiliser les fonctionnalités combinées pour assembler et héberger un flux en direct.

Ces serveurs disposent ainsi d&#39;une interface de fichiers unifiée leur permettant de s&#39;exécuter facilement sur un seul ordinateur. Il continue d’offrir la souplesse nécessaire pour être configuré en tant qu’Origine ou Packager distinct.

**Prise en charge bêta MPEG-DASH**

Primetime Streaming Server prend en charge les packages MPEG-DASH pour les workflows en direct et VOD. Le composant Live Packager convertit les flux RTMP ou MPEG-2-TS d’assimilation au format DASH. Le composant Origine accepte un flux DASH.

Pour les workflows VOD, le composant Offline Packager convertit les fichiers MP4 et TS au format ISOBFF MPEG-DASH.

**Conversion en direct vers VOD**

Un nouveau composant Recording Server est désormais disponible, qui prend en charge la capture d’un flux en direct et l’archivage pour la lecture VOD. Il prend en charge la création de lectures de Événement complet ainsi que de clips/temps forts pour une partie du événement. Il peut être configuré pour enregistrer des flux audio uniquement, supprimer des publicités ou des tranches dans du contenu en direct. Recording Server fonctionne avec Primetime Streaming Server ainsi qu’avec des Origines tierces.

**Conversion RTMP vers HLS dans Primetime Live Packager**

Le composant Primetime Live Packager prend en charge la création de flux HLS à partir de flux RTMP. Il permet également d&#39;ajouter le DRM Primetime et la diffusion en continu protégée aux flux HLS de sortie.

**Authentification des flux RTMP entrants vers Primetime Live Packager**

Un fichier usermgmt.jar est désormais livré avec Primetime Live Packager pour configurer l’accès avec des informations d’identification de confiance lors de l’envoi d’un flux RTMP à Primetime Live Packager.

Désormais, les encodeurs peuvent être configurés pour utiliser un nom d’utilisateur/mot de passe lors de l’envoi de flux vers Live Packager.

**Outil PlaylistCreator pour créer des manifestes de niveau supérieur pour HDS et HLS**

L’utilitaire PlaylistCreator.jar est désormais disponible avec Primetime Offline Packager pour créer facilement des fichiers de manifeste de niveau supérieur pour les ressources HDS et HLS.

**Fonctionnalité de sécurité supplémentaire pour l&#39;intégration d&#39;un module de sécurité matérielle**

Primetime Offline Packager prend désormais en charge l’accès au certificat d’identification de Packager et aux clés communes à partir d’un module de sécurité matérielle.

Un module de sécurité matérielle fournit une protection supplémentaire à ces ressources confidentielles.

**Performances améliorées pour l&#39;empaquetage VOD**

Plusieurs améliorations de performances ont été apportées afin d’améliorer le délai de création des fichiers mezzanine dans Primetime Offline Packager.

**Performances améliorées pour l’empaquetage JIT MP4**

Plusieurs améliorations de performances ont été apportées aux fonctionnalités d’emballage JIT de Primetime Origine pour gérer les demandes d’utilisateurs concernant une grande bibliothèque de ressources VOD.

## Adobe Primetime Streaming Server 1.4 {#adobe-primetime-streaming-server}

### Configuration minimale requise {#minimum-system-requirements}

**Configuration réseau requise**

* La multidiffusion réseau doit être activée pour envoyer le flux MPEG-TS d’un encodeur à Live Packager. Live Packager accepte également un flux RTMP provenant d’un encodeur qui ne nécessite pas de réseau à diffusion multiple.

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon® double ou plus rapide recommandé)
* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandés)
* Carte Ethernet 1 Gb recommandée (plusieurs cartes réseau et 10 Gb également pris en charge)
* Disque :

   * (Disk-SAS) : 10 Go minimum avec 7,5 000 tr/min
   * (Disk-SSD) : 400 Mops en lecture/écriture
   * (NAS) : 1 Go de lien dédié

**Configuration logicielle requise**

* Oracle Java JRE 1.7 (Recommandé : JVM Sun/Oracle Hotspot). Le JDK est requis pour l’accès de JConsole aux API JMX.

### Installation et configuration de Primetime Streaming Server {#install-and-configure-primetime-streaming-server}

**Installation du serveur de flux continu**

1. Téléchargez le logiciel Java SE et JDK sur le site [](https://www.oracle.com/technetwork/java/javase/downloads/index.html) Oracle et suivez les instructions d’installation.
2. Extrayez le fichier d’archive Adobe Primetime-Streaming Server 1.4 `Primetime- StreamingServer-1-4-0-b206-12042014.zip` sur votre disque.

**Début du serveur de flux continu Primetime**

Pour début au serveur de diffusion en continu, exécutez la commande suivante à partir de la ligne de commande du répertoire racine du serveur de diffusion en continu :\
`$./pss_start.sh`

**Configuration du serveur de flux continu Primetime en tant que serveur d’Origine HTTP ou Live Packager**

Pour configurer le serveur de flux continu en tant que Live Packager ou Origine Server, mettez à jour le fichier de configuration pss.xml placé dans le répertoire conf du répertoire racine du serveur de flux continu :

```
<Config> 
<!-- Set this false to disable the Origin Component. --> 
<OriginEnabled&gt;true&lt;/OriginEnabled>  
<!-- Set this false to disable the Packager Component. -->  
<PackagerEnabled&gt;true&lt;/PackagerEnabled>
</Config>
```

**Arrêt du serveur de diffusion en continu Primetime**

Pour arrêter le serveur de diffusion en continu, exécutez la commande suivante dans le répertoire racine du serveur de diffusion en continu :\
`$./pss_stop.sh`

**Redémarrage du serveur de diffusion en continu Primetime**

Pour redémarrer le serveur de diffusion en continu, arrêtez et début le serveur de diffusion en continu.

<!-- 

Comment Type: draft

**Configuring Primetime Streaming Server**

Refer the Primetime Streaming Server Getting Started document for the configuration details available at [https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf](https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf).

-->

**Désinstallation du serveur de diffusion en continu Primetime**

Pour désinstaller le serveur de diffusion en continu, arrêtez le serveur de diffusion en continu et supprimez le répertoire pss du serveur de diffusion en continu dans le répertoire Primetime.

## Utilisation de Live Packager et Origine Server 1.4 {#working-with-live-packager-and-origin-server}

Cette section s’applique lorsque Primetime Streaming Server n’est pas utilisé et que Primetime Live Packager ET/OU Primetime Origine Server est déployé.

### Configuration minimale requise {#minimum-system-requirements-1}

**Configuration réseau requise**

* La multidiffusion réseau doit être activée pour envoyer le flux MPEG-TS d’un encodeur à Live Packager. Live Packager accepte également un flux RTMP provenant d’un encodeur qui ne nécessite pas de réseau à diffusion multiple.

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon® double ou plus rapide recommandé)
* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandés)
* Carte Ethernet 1 Gb recommandée (plusieurs cartes réseau et 10 Gb également pris en charge)
* Disque :

   * (Disk-SAS) : 10 Go minimum avec 7,5 000 tr/min
   * (Disk-SSD) : 400 Mops en lecture/écriture
   * (NAS) : 1 Go de lien dédié

**Configuration logicielle requise**

* Oracle Java JRE 1.7 (Recommandé : JVM Sun/Oracle Hotspot). Le JDK est requis pour l’accès de JConsole aux API JMX.

La configuration minimale requise ci-dessus est vraie pour Origine Server et Live Packager.

### Installation et configuration de Live Packager {#install-and-configure-the-live-packager}

**Installation de Live Packager**

1. Téléchargez le logiciel Java SE et JDK sur le site [](https://www.oracle.com/technetwork/java/javase/downloads/index.html) Oracle et suivez les instructions d’installation.
1. Extrayez le fichier d’archive Adobe Primetime - Live Packager 1.4 `Primetime-LivePackager-1-4-0-b206-12042014.zip` sur votre disque.

**Installation du serveur d’Origines HTTP**

1. Téléchargez le logiciel Java JRE et JDK sur le site [](https://www.oracle.com/technetwork/java/javase/downloads/index.html) Oracle et suivez les instructions d’installation.
1. Extrayez sur votre disque le fichier d’archive Adobe Primetime - HTTP Origine Server 1.4 `Primetime-HttpOrigin-1-4-0-b206-12042014.zip`.

**Pour début à Live Packager** Pour début à l’outil de création de package, exécutez la commande suivante à partir du répertoire racine de l’outil de création de package :\
`$packager_start.sh`

**Pour début du serveur d’Origines HTTP**

Pour début au serveur d’Origines HTTP, exécutez la commande suivante à partir de la ligne de commande du répertoire racine du serveur d’Origines :\
`$./origin_start.sh`

**Arrêt de Live Packager**

Pour arrêter le gestionnaire de package, exécutez la commande suivante à partir du répertoire racine du gestionnaire de package :\
`$packager_stop.sh`

**Arrêt du serveur d’Origines HTTP**

Pour arrêter le serveur d’Origines HTTP, exécutez la commande suivante dans le répertoire racine du serveur d’Origines :\
`$./origin_stop.sh`

**Redémarrage de Live Packager**

Pour redémarrer le gestionnaire de package, arrêtez-le et début-le.

**Remarque**: Lorsque l’outil de création de package début, il tente d’initialiser les informations d’amorçage à partir de la cible de fragments dans le répertoire temporaire. Si les informations d’amorçage se trouvent à la cible du fragment, cela signifie que le packager a été redémarré. En cas de redémarrage, l’outil de création de package attend la limite de fragment suivante, puis début la création de package. Le gestionnaire de package insère une entrée d’espace dans l’amorçage pour indiquer qu’il manque des fragments.

**Redémarrage du serveur d’Origines HTTP**

Pour redémarrer le serveur d’Origines HTTP, arrêtez et début le serveur d’Origines HTTP.

**Configuration de Live Packager**

Le fichier de distribution contient un exemple de configuration qui peut être utilisé pour tester l’outil de création de package.

Après avoir extrait l’archive Adobe Primetime - Live Packager 1.4, remplacez les répertoires par le répertoire packager et exécutez le script packager_début.sh. L’exemple de configuration écoute l’adresse de multidiffusion 239.235.0.3:14000 et exécute le serveur d’origine local sur le port 8080. La sortie est configurée pour être écrite dans le `packager/webroot/_default_/_default_/ directory`.

<!-- 

Comment Type: draft

For more details about the configuration refer [the Primetime Live Packager document](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

-->

**Configuration du serveur d’Origines HTTP**

Consultez le document de démarrage de Primetime HTTP Origine Server pour obtenir les détails de configuration disponibles ici.

**Désinstallation de Live Packager**

Pour désinstaller le gestionnaire de package, arrêtez-le et supprimez le répertoire de ce dernier du répertoire Primetime.

**Désinstallation du serveur d’Origines HTTP**

Pour désinstaller le serveur d’Origines HTTP, arrêtez le serveur d’Origines HTTP et supprimez le répertoire d’origine du serveur d’Origines HTTP dans le répertoire Primetime.

## Adobe Primetime Offline Packager 1.4 {#adobe-primetime-offline-packager}

### Configuration minimale requise {#minimum-system-requirements-2}

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon® double ou plus rapide recommandé)
* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandés)
* Carte Ethernet 1 Gb recommandée (plusieurs cartes réseau et 10 Gb également pris en charge)
* Disque :

   * (Disk-SAS) : 10 Go minimum avec 7,5 000 tr/min
   * (Disk-SSD) : 400 Mops en lecture/écriture
   * (NAS) : 1 Go de lien dédié

**Configuration logicielle requise**

* Oracle Java JRE 1.7 ou version ultérieure.

### Installation et configuration de Offline Packager {#install-and-configure-offline-packager}

Pour installer Offline Packager, procédez comme suit :

1. Téléchargez le logiciel Java SE sur le site [](https://www.oracle.com/technetwork/java/javase/downloads/index.html) Oracle et suivez les instructions d&#39;installation.
1. Extrayez le fichier d’archive Adobe Primetime - Offline Packager 1.4 `Primetime- OfflinePackager-1-4-0-b206-12042014.zip`sur votre disque.

Reportez-vous au document de prise en main de Primetime Offline Packager pour obtenir les détails de configuration disponibles [ici](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète sur la page de formation et d’assistance [](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.