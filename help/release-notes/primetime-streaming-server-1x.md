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
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Versions de Primetime Streaming Server {#primetime-streaming-server-x-releases}

Nouveautés des versions 1.3 et 1.4 de Primetime Streaming Server.

## Nouveautés de Primetime Streaming Server 1.4 (version de décembre) {#what-s-new-in-primetime-streaming-server-december-release}

**Packager hors ligne**

* Les flux HLS de sortie contiennent désormais des métadonnées ID3 présentes dans MPEG-2 TS
* Les flux audio HLS uniquement peuvent désormais avoir une image statique associée
* Prise en charge de la prise en charge de IV en tant qu’entrée utilisateur pour le de chiffrement AES HLS 
* Prise en charge de la sortie IV dans un fichier lorsque IV est généré par le gestionnaire de package hors ligne
* Playlist Creator prend désormais en charge l’association de groupes audio multilingues et de groupes de sous-titres WebVTT multilingues aux flux média.

**serveur**

* Le chiffrement AES HLS est disponible pour les  en direct et VOD.  Primetime  peut appliquer le chiffrement HLS AES à des flux HLS ou des fichiers MP4 entrants.
* Il peut également appliquer le chiffrement JIT HLS AES lorsqu’il est utilisé pour convertir des flux HDS entrants en flux HLS.
* Primetime  prend désormais en charge la liste blanche SWF pour les flux PHLS. Auparavant, il était uniquement pris en charge pour les flux de SPHD.

**Primetime Live Packager**

* Prise en charge de la génération de flux HLS AES-128 pour les flux RTMP et MPEG-2 TS d’entrée

Les certificats PHDS/PHLS ont été actualisés. La même date d&#39;expiration sera le 01/10/2016.

### **Correctifs inclus dans la version 1.4**{#bug-fixes-included-in-release}

* PTPUB-282- Le manifeste de niveau HLS créé par OfflinePackager 1.3.1 ne contient pas d’informations de codec et de résolution.
* PTPUB-353 - PlayListCreator ne prend pas en charge l’ajout d’informations WebVTT dans le manifeste de niveau défini.
* PTPUB-583 - L’outil PlaylistCreator ajoute de manière inattendue les URI du groupe avec.
* PTPUB-605 Playlist Creator ne répertoriant pas le groupe SOUS-TITRE dans chaque flux de variante
* PTPUB-634 -Offline Packager ajoute SpliceInsert au manifeste.
* PTPUB-635 - Plusieurs balises SpliceOut insérées pour une seule annonce.

### Problème connu dans la version 1.4 {#known-issue-in-release}

* PTPUB- 645 Le mode Imple DPIS est imposé même lorsque le mode DPIScte35 est spécifié lorsque les repères de ligne de commande et les signaux in-stream sont tous deux fournis dans la configuration du gestionnaire de package hors ligne.

## Nouveautés de Primetime Streaming Server 1.3.1 (version MAI) {#what-s-new-in-primetime-streaming-server-may-release}

La version 1.3.1 fait référence au correctif. Les améliorations suivantes en font une mise à niveau recommandée pour les clients, car elle consiste en des améliorations de performances clés pour les cas d’utilisation de JIT MP4 :

1. Correctif de performances de la génération m3u8 MP4 JIT sur   avec DRM incluant la rotation de clé
1. Ajout d’une configuration &quot;CopyQueryParamToJITFragmentURIs&quot; pour copier  paramètres de la demande de manifeste JIT vers les URI de fragment générés pour la conversion JIT MP4. Reportez-vous à la documentation HTTP   Server pour obtenir des exemples d’utilisation
1. Autoriser les fichiers MP4 sans extension pour la conversion JIT, via la configuration Config/MP4Only ajoutée au fichier vod.xml

### Correctifs inclus dans la version 1.3.1 {#bug-fixes-included-in-release-1}

* 3759167 - Certains indices SCTE35 ne parviennent pas au manifeste de sortie en raison d’une anomalie d’horodatage lors de l’assemblage. Appliquez pts_réglage sur SpliceTime dans le TimeSignal de SpliceInfoSection dans le message SCTE35.

### Problèmes connus dans la version 1.3.1 {#known-issues-in-release}

* 3717039 - Lorsque l’outil de création de packages est configuré pour produire des repères de mode simple ppp, il doit en fait rechercher des types de signaux spécifiques, tels que l’insertion de splice ou l’opportunité de placement, et convertir uniquement ceux-ci en signaux de mode simple. Il doit ignorer d&#39;autres types de signaux tels que les  de l&#39;, les  du réseau, etc.

* 3718598 - Lorsque  serveur  est configuré pour diffuser des contenus protégés avec un accès HSM activé, le client LunaSA principal communique fréquemment avec le module HSM

## Nouveautés de Primetime Streaming Server 1.3 (version d’AVRIL) {#what-s-new-in-primetime-streaming-server-april-release}

La version 1.3 de Primetime offre plusieurs nouvelles fonctionnalités liées à la diffusion en flux continu de contenu, ainsi qu’une meilleure convivialité et une meilleure sécurité.

**Serveur de diffusion en flux continu Primetime en tant que forme unifiée de Live Packager et de  serveur**

Primetime Live Packager et Primetime   sont regroupés pour fonctionner comme un composant unique. Ce composant peut être utilisé en tant que Packager ou en tant que   ou utiliser les fonctionnalités combinées pour compresser et héberger un flux en direct.

Ces serveurs disposent ainsi d’une interface de fichiers unifiée leur permettant de s’exécuter facilement sur un seul ordinateur. Il continue à offrir la flexibilité nécessaire pour être configuré en tant que Packager ou distinct.

**Prise en charge Bêta MPEG-DASH**

Primetime Streaming Server prend en charge l’assemblage MPEG-DASH pour les  en direct et VOD. Le composant Live Packager convertit les flux RTMP ou MPEG-2-TS d’assimilation au format DASH. Le composant   accepte un flux DASH.

Pour les  VOD, le composant Offline Packager convertit les fichiers MP4 et TS au format ISOBFF MPEG-DASH.

**Conversion en direct vers VOD**

Un nouveau composant Recording Server est désormais disponible, qui prend en charge la capture d’un flux en direct et l’archivage pour la lecture VOD. Il prend en charge la création de lectures  complètes ainsi que de clips/surbrillances pour une partie du  de. Il peut être configuré pour enregistrer des flux audio uniquement, supprimer des publicités ou des tranches dans du contenu en direct. Le serveur d’enregistrement fonctionne avec le serveur de diffusion en flux continu Primetime ainsi qu’avec des tiers  .

**Conversion RTMP vers HLS dans Primetime Live Packager**

Le composant Primetime Live Packager prend en charge la création de flux HLS à partir de flux RTMP. Il permet également d’ajouter le DRM Primetime et la diffusion en continu protégée aux flux HLS de sortie.

**Authentification des flux RTMP entrants vers Primetime Live Packager**

Un fichier usermgmt.jar est désormais fourni avec Primetime Live Packager pour configurer l’accès avec des informations d’identification de confiance lors de l’envoi d’un flux RTMP vers Primetime Live Packager.

Désormais, les encodeurs peuvent être configurés pour utiliser un nom d’utilisateur/mot de passe lors de l’envoi de flux vers Live Packager.

**Outil PlaylistCreator pour créer des manifestes de niveau supérieur pour HDS et HLS**

L’utilitaire PlaylistCreator.jar est désormais disponible avec Primetime Offline Packager pour créer facilement des fichiers de manifeste de niveau supérieur pour les ressources HDS et HLS.

**Fonction de sécurité supplémentaire pour intégrer un module de sécurité matérielle**

Primetime Offline Packager prend désormais en charge l’accès au certificat d’identification et aux clés communes de Packager à partir d’un module de sécurité matérielle.

Un module de sécurité matérielle offre une protection supplémentaire à ces fichiers confidentiels.

**Performances améliorées pour l&#39;assemblage VOD**

Plusieurs améliorations ont été apportées aux performances afin d’améliorer le délai de création des fichiers mezzanine dans Primetime Offline Packager.

**Performances améliorées pour l’assemblage MP4 JIT**

Plusieurs améliorations de performances ont été apportées aux fonctionnalités d’empaquetage JIT de Primetime  les pour traiter les demandes des utilisateurs concernant une grande bibliothèque de ressources VOD.

## Adobe Primetime Streaming Server 1.4 {#adobe-primetime-streaming-server}

### Configuration minimale requise {#minimum-system-requirements}

**Configuration réseau requise**

* La multidiffusion réseau doit être activée pour envoyer le flux MPEG-TS depuis un encodeur vers Live Packager. Live Packager accepte également un flux RTMP provenant d’un encodeur qui ne nécessite pas de réseau à diffusion multiple.

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon® double ou plus rapide recommandé)
* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandés)
* Carte Ethernet 1 Go recommandée (plusieurs cartes réseau et 10 Go également pris en charge)
* Disque :

   * (Disk-SAS) : 10 Go minimum avec 7,5 000 tr/min
   * (Disk-SSD) : 400 Mops de lecture/écriture
   * (NAS) : Lien dédié 1 Go

**Configuration logicielle requise**

* Oracle Java JRE 1.7 (Recommandé : JVM Sun/Oracle Hotspot). Le JDK est requis pour l’accès JConsole aux API JMX.

### Installation et configuration de Primetime Streaming Server {#install-and-configure-primetime-streaming-server}

**Installation du serveur de flux continu**

1. Téléchargez le logiciel Java SE et JDK depuis le site [](https://www.oracle.com/technetwork/java/javase/downloads/index.html) Oracle et suivez les instructions d’installation.
2. Extrayez le fichier d’archive Adobe Primetime-Streaming Server 1.4 `Primetime- StreamingServer-1-4-0-b206-12042014.zip` sur votre disque.

**du serveur de diffusion en flux continu Primetime**

Pour  le serveur de diffusion en continu, exécutez la commande suivante à partir de la ligne de commande du répertoire racine du serveur de diffusion en continu :\
`$./pss_start.sh`

**Configuration du serveur de diffusion en flux continu Primetime en tant que serveur de Live Packager ou HTTP**

Pour configurer le serveur de diffusion en continu en tant que serveur Live Packager ou  serveur , mettez à jour le fichier de configuration pss.xml placé dans le répertoire conf du répertoire racine du serveur de diffusion en continu :

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

Pour redémarrer le serveur de diffusion en continu, arrêtez et le serveur de diffusion en continu.

<!-- 

Comment Type: draft

**Configuring Primetime Streaming Server**

Refer the Primetime Streaming Server Getting Started document for the configuration details available at [https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf](https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf).

-->

**Désinstallation du serveur de diffusion en continu Primetime**

Pour désinstaller le serveur de diffusion en continu, arrêtez le serveur de diffusion en continu et supprimez le répertoire pss du serveur de diffusion en continu dans le répertoire Primetime.

## Utilisation de Live Packager et   Server 1.4 {#working-with-live-packager-and-origin-server}

Cette section s’applique lorsque Primetime Streaming Server n’est pas utilisé et que Primetime Live Packager ET/OU Primetime  le serveur  est en cours de déploiement.

### Configuration minimale requise {#minimum-system-requirements-1}

**Configuration réseau requise**

* La multidiffusion réseau doit être activée pour envoyer le flux MPEG-TS depuis un encodeur vers Live Packager. Live Packager accepte également un flux RTMP provenant d’un encodeur qui ne nécessite pas de réseau à diffusion multiple.

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon® double ou plus rapide recommandé)
* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandés)
* Carte Ethernet 1 Go recommandée (plusieurs cartes réseau et 10 Go également pris en charge)
* Disque :

   * (Disk-SAS) : 10 Go minimum avec 7,5 000 tr/min
   * (Disk-SSD) : 400 Mops de lecture/écriture
   * (NAS) : Lien dédié 1 Go

**Configuration logicielle requise**

* Oracle Java JRE 1.7 (Recommandé : JVM Sun/Oracle Hotspot). Le JDK est requis pour l’accès JConsole aux API JMX.

La configuration minimale requise ci-dessus est vraie pour  serveur  ainsi que pour Live Packager.

### Installation et configuration de Live Packager {#install-and-configure-the-live-packager}

**Installation de Live Packager**

1. Téléchargez le logiciel Java SE et JDK depuis le site [](https://www.oracle.com/technetwork/java/javase/downloads/index.html) Oracle et suivez les instructions d’installation.
1. Extrayez le fichier d’archive Adobe Primetime - Live Packager 1.4 `Primetime-LivePackager-1-4-0-b206-12042014.zip` sur votre disque.

**Installation du serveur HTTP**

1. Téléchargez le logiciel Java JRE et JDK depuis le site [](https://www.oracle.com/technetwork/java/javase/downloads/index.html) Oracle et suivez les instructions d’installation.
1. Extrayez sur votre disque le fichier d’archive Adobe Primetime - HTTP   Server 1.4 `Primetime-HttpOrigin-1-4-0-b206-12042014.zip`.

**Pour  l’outil Live Packager** Pour  l’outil de création de package, exécutez la commande suivante à partir du répertoire racine de l’outil de création de package :\
`$packager_start.sh`

**Pour  le serveur HTTP**

Pour  le serveur HTTP  , exécutez la commande suivante à partir de la ligne de commande du répertoire racine du serveur de:\
`$./origin_start.sh`

**Arrêt de Live Packager**

Pour arrêter le gestionnaire de package, exécutez la commande suivante à partir du répertoire racine du gestionnaire de package :\
`$packager_stop.sh`

**Arrêtez le serveur HTTP**

Pour arrêter le serveur HTTP  , exécutez la commande suivante dans le répertoire racine du serveur de  de la  :\
`$./origin_stop.sh`

**Redémarrage de Live Packager**

Pour redémarrer le gestionnaire de package, arrêtez et le gestionnaire de package.

**Remarque**: Lorsque le de packager , il tente d’initialiser les informations d’amorçage à partir du de fragments  dans le répertoire temporaire. Si les informations d’amorçage se trouvent dans le de fragments, cela signifie que le programme de mise en package a été redémarré. En cas de redémarrage, l’outil de création de package attend la prochaine limite du fragment, puis  l’assemblage. Le gestionnaire de package insère une entrée d’espace dans l’amorçage pour indiquer qu’il manque des fragments.

**Redémarrez le serveur HTTP**

Pour redémarrer le serveur HTTP  , arrêtez et le serveur HTTP de.

**Configuration de Live Packager**

Le fichier de distribution contient un exemple de configuration qui peut être utilisé pour tester le gestionnaire de package.

Après avoir extrait l’archive Adobe Primetime - Live Packager 1.4, remplacez les répertoires par le répertoire packager et exécutez le script packager_.sh. L’exemple de configuration écoute l’adresse de multidiffusion 239.235.0.3:14000 et exécute le serveur de  de  local sur le port 8080. La sortie est configurée pour être écrite dans le `packager/webroot/_default_/_default_/ directory`.

<!-- 

Comment Type: draft

For more details about the configuration refer [the Primetime Live Packager document](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

-->

**Configuration du serveur de HTTP**

Reportez-vous au  HTTP  Primetime  Server Getting Started pour obtenir les détails de configuration disponibles ici.

**Désinstallation de Live Packager**

Pour désinstaller le gestionnaire de package, arrêtez-le et supprimez le répertoire de ce dernier du répertoire Primetime.

**Désinstallation du serveur HTTP**

Pour désinstaller le serveur HTTP  , arrêtez le serveur HTTP  et supprimez le répertoire d’origine du serveur deHTTP dans le répertoire Primetime.

## Adobe Primetime Offline Packager 1.4 {#adobe-primetime-offline-packager}

### Configuration minimale requise {#minimum-system-requirements-2}

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon® double ou plus rapide recommandé)
* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandés)
* Carte Ethernet 1 Go recommandée (plusieurs cartes réseau et 10 Go également pris en charge)
* Disque :

   * (Disk-SAS) : 10 Go minimum avec 7,5 000 tr/min
   * (Disk-SSD) : 400 Mops de lecture/écriture
   * (NAS) : Lien dédié 1 Go

**Configuration logicielle requise**

* Oracle Java JRE 1.7 ou version ultérieure.

### Installation et configuration de Offline Packager {#install-and-configure-offline-packager}

Pour installer Offline Packager, procédez comme suit :

1. Téléchargez le logiciel Java SE à partir du site [](https://www.oracle.com/technetwork/java/javase/downloads/index.html) Oracle et suivez les instructions d&#39;installation.
1. Décompressez le fichier d’archive Adobe Primetime - Offline Packager 1.4 `Primetime- OfflinePackager-1-4-0-b206-12042014.zip`sur votre disque.

Reportez-vous au  de prise en main de Primetime Offline Packager pour obtenir les détails de configuration disponibles [ici](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

## Ressources utiles {#helpful-resources}

* Reportez-vous à la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.