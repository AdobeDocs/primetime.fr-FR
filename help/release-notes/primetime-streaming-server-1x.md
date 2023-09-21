---
title: Versions de Primetime Streaming Server
description: Nouveautés des versions 1.3 et 1.4 de Primetime Streaming Server.
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1916'
ht-degree: 0%

---

# Versions de Primetime Streaming Server {#primetime-streaming-server-x-releases}

Nouveautés des versions 1.3 et 1.4 de Primetime Streaming Server.

## Nouveautés de Primetime Streaming Server 1.4 (version de décembre) {#what-s-new-in-primetime-streaming-server-december-release}

**Packager hors ligne**

* Les flux HLS de sortie contiennent désormais des métadonnées ID3 présentes dans MPEG-2 TS
* Les diffusions HLS Audio uniquement peuvent désormais avoir une image statique associée.
* Prise en charge de la prise en charge d’IV en tant qu’entrée utilisateur pour les workflows de chiffrement HLS AES
* Prise en charge de la sortie IV dans un fichier lorsque IV est généré par le module de package hors ligne
* Le créateur de liste de lecture prend désormais en charge l’association de groupes audio multilingues et de groupes de sous-titres WebVTT multilingues aux flux multimédia.

**Serveur d’origine**

* Le cryptage HLS AES est disponible pour les workflows Live et VOD. Primetime Origin peut appliquer le chiffrement HLS AES à des flux HLS ou à des fichiers MP4 entrants.
* Il peut également appliquer le chiffrement JIT HLS AES lorsqu’il est utilisé pour convertir les flux HDS entrants en flux HLS.
* Primetime Origin prend désormais en charge les listes autorisées de SWF pour les flux PHLS. Auparavant, il était uniquement pris en charge pour les flux de SPHDS.

**Primetime Live Packager**

* Prise en charge de la génération de flux HLS AES-128 pour les flux RTMP d’entrée et MPEG-2 TS

Les certificats PHDS/PHLS ont été actualisés. La nouvelle date d’expiration du même événement sera 10/01/2016.

### **Correctifs inclus dans la version 1.4** {#bug-fixes-included-in-release}

* PTPUB-282 - Le manifeste de niveau HLS créé par OfflinePackager 1.3.1 ne comporte pas d’informations de codec et de résolution.
* PTPUB-353 - PlayListCreator ne prend pas en charge l’ajout d’informations WebVTT dans le manifeste de niveau fixe.
* PTPUB-583 - L’outil PlaylistCreator ajoute de manière inattendue les URI de groupe à .
* PTPUB-605 Playlist Creator ne répertoriant pas le groupe SUBTITLE dans chaque flux de variante
* PTPUB-634 - Offline Packager ajoute SpliceInsert au manifeste.
* PTPUB-635 - Plusieurs balises SpliceOut insérées pour une seule notification.

### Problème connu dans la version 1.4 {#known-issue-in-release}

* Le mode PTPUB-645 DPISimple est forcé même lorsque le mode DPIScte35 est spécifié lorsque les signaux de ligne de commande et les signaux en flux continu sont fournis dans la configuration du package hors ligne.

## Nouveautés de Primetime Streaming Server 1.3.1 (version de MAI) {#what-s-new-in-primetime-streaming-server-may-release}

La version 1.3.1 fait référence au correctif. Les améliorations suivantes en font une mise à niveau recommandée pour les clients, car elle comprend des améliorations de performances clés pour les cas d’utilisation JIT MP4 :

1. Correctif de performance pour la génération MP4 JIT m3u8 à l’origine avec DRM, y compris la rotation de clé
1. Ajout d’une configuration &quot;CopyQueryParamToJITFragmentURIs&quot; pour copier les paramètres de requête de la demande de manifeste JIT vers les URI de fragment générés pour la conversion MP4 JIT. Consultez la documentation du serveur d’origine HTTP pour obtenir un exemple d’utilisation
1. Autorisation des fichiers MP4 sans extension pour la conversion JIT , via la configuration Config/MP4Only ajoutée à vod.xml

### Correctifs inclus dans la version 1.3.1 {#bug-fixes-included-in-release-1}

* 3759167 - Tous les indicateurs SCTE35 ne sont pas parvenus au manifeste de sortie en raison d’une anomalie de l’horodatage lors du conditionnement. Appliquez l’ajustement points sur SpliceTime dans le message TimeSignal de SpliceInfoSection dans SCTE35.

### Problèmes connus dans la version 1.3.1 {#known-issues-in-release}

* 3717039 - Lorsque le programme de package est configuré pour produire des repères de mode simple en ppp, il doit vraiment rechercher des types de signaux spécifiques, tels que des éclats ou des opportunités de placement, et convertir uniquement ceux-ci en repères de mode simple. Il doit ignorer d’autres types de signaux tels que le démarrage du programme, le démarrage du réseau, etc.

* 3718598 - Lorsque le serveur d’origine est configuré pour diffuser des contenus protégés avec l’accès HSM activé, le client LunaSA principal communique fréquemment avec le module HSM.

## Nouveautés de Primetime Streaming Server 1.3 (version d’AVRIL) {#what-s-new-in-primetime-streaming-server-april-release}

La version 1.3 de Primetime comprend plusieurs nouvelles fonctionnalités relatives au contenu en flux continu, à une meilleure convivialité et à une meilleure sécurité.

**Serveur de diffusion en continu Primetime en tant que forme unifiée de Live Packager et du serveur d’origine**

Primetime Live Packager et Primetime Origin sont rassemblés pour fonctionner comme un seul composant. Ce composant peut être utilisé comme Packager ou comme origine ou utiliser les fonctionnalités combinées pour regrouper et héberger un Live Stream.

Cela fournit une interface de fichier unifiée à ces serveurs, ce qui les rend faciles à exécuter sur une seule machine. Il offre toujours la possibilité d’être configuré en tant que Packager ou Origin distinct.

**Prise en charge bêta MPEG - DASH**

Primetime Streaming Server prend en charge le package MPEG-DASH pour les workflows Live et VOD. Le composant de package en direct convertit les flux RTMP ou MPEG-2-TS d’ingestion au format DASH. Le composant Origin accepte un flux DASH.

Pour les processus VOD, le composant Offline Packager convertit les ressources MP4 et TS au format MPEG-DASH ISOBFF.

**Conversion en direct vers VOD**

Un nouveau serveur d’enregistrement de composant est désormais disponible. Il prend en charge la capture d’un flux en direct et l’archivage pour la lecture VOD. Il prend en charge la création de lectures d’événement complètes, ainsi que de clips/temps forts pour une partie de l’événement. Il peut être configuré pour enregistrer des diffusions audio uniquement, supprimer des publicités ou des étiquettes dans du contenu en direct. Le serveur d’enregistrement fonctionne avec Primetime Streaming Server ainsi qu’avec des Origines tierces.

**Conversion RTMP vers HLS dans Primetime Live Packager**

Le composant Primetime Live Packager prend en charge la création de flux HLS à partir de flux RTMP. Il permet également d’ajouter Primetime DRM et Protected Streaming aux flux HLS de sortie.

**Authentification pour les flux RTMP entrants vers Primetime Live packager**

Un usermgmt.jar est désormais fourni avec Primetime Live Packager pour configurer l’accès avec des informations d’identification de confiance lors de l’envoi d’un flux RTMP à Primetime Live Packager.

Désormais, les encodeurs peuvent être configurés pour utiliser un nom d’utilisateur/mot de passe lors de l’envoi de flux vers Live Packager.

**Outil PlaylistCreator pour créer des manifestes de niveau supérieur pour HDS et HLS**

Un utilitaire performant PlaylistCreator.jar est désormais disponible avec Primetime Offline Packager afin de créer facilement des fichiers manifestes de niveau supérieur pour les ressources HDS et HLS.

**Fonctionnalité de sécurité supplémentaire pour incorporer un module de sécurité matérielle**

Primetime Offline Packager prend désormais en charge l’accès au certificat d’identification de Packager et aux clés communes à partir d’un module de sécurité matérielle.

Un module de sécurité matérielle fournit une protection supplémentaire à ces ressources confidentielles.

**Amélioration des performances pour les modules VOD**

Plusieurs améliorations de performances ont été apportées afin d’améliorer le délai de création des ressources mezzanine dans le Primetime Offline Packager.

**Amélioration des performances de la mise en package JIT MP4**

Plusieurs améliorations de performances ont été apportées aux fonctionnalités de regroupement JIT de Primetime Origin afin de gérer les demandes des utilisateurs pour une bibliothèque volumineuse de ressources VOD.

## Adobe Primetime Streaming Server 1.4 {#adobe-primetime-streaming-server}

### Configuration minimale requise {#minimum-system-requirements}

**Configuration requise**

* La multidiffusion réseau doit être activée pour envoyer la diffusion MPEG-TS d’un encodeur vers Live Packager. Live Packager accepte également un flux RTMP provenant d’un encodeur qui ne nécessite pas de réseau à diffusion multiple.

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon double ® ou plus rapide recommandé)
* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandé)
* Carte Ethernet 1 Go recommandée (plusieurs cartes réseau et 10 Go également pris en charge)
* Disque :

   * (Disk-SAS) : 10 Go minimum avec 7,5 K tr/min
   * (Disque-SSD) : 400 Mbit/s en lecture/écriture
   * (NAS) : lien dédié 1 Go

**Exigences logicielles**

* Oracle Java JRE 1.7 (Recommandé : JVM Sun/Oracle Hotspot). Le JDK est requis pour l’accès de JConsole aux API JMX.

### Installation et configuration du serveur de diffusion Primetime {#install-and-configure-primetime-streaming-server}

**Installation du serveur de diffusion en continu**

1. Téléchargez le logiciel Java SE et JDK à partir du [Oracle site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) et suivez les instructions d’installation.
2. Extrayez le fichier d’archive Adobe Primetime-Streaming Server 1.4, `Primetime- StreamingServer-1-4-0-b206-12042014.zip` sur votre disque.

**Démarrage du serveur de diffusion Primetime**

Pour démarrer le serveur de diffusion en continu, exécutez la commande suivante à partir de la ligne de commande du répertoire racine du serveur de diffusion en continu :\
`$./pss_start.sh`

**Configuration du serveur de diffusion Primetime en tant que serveur Live Packager ou HTTP Origin**

Pour configurer le serveur de diffusion en continu comme Live Packager ou Origin Server, mettez à jour le fichier de configuration pss.xml situé dans le répertoire conf du répertoire racine du serveur de diffusion en continu :

```
<Config> 
<!-- Set this false to disable the Origin Component. --> 
<OriginEnabled&gt;true&lt;/OriginEnabled>  
<!-- Set this false to disable the Packager Component. -->  
<PackagerEnabled&gt;true&lt;/PackagerEnabled>
</Config>
```

**Arrêt du serveur de diffusion Primetime**

Pour arrêter le serveur de diffusion en continu, exécutez la commande suivante dans le répertoire racine du serveur de diffusion en continu :\
`$./pss_stop.sh`

**Redémarrage du serveur de diffusion Primetime**

Pour redémarrer le serveur de diffusion en continu, arrêtez le serveur de diffusion en continu et démarrez-le.

<!-- 

Comment Type: draft

**Configuring Primetime Streaming Server**

Refer the Primetime Streaming Server Getting Started document for the configuration details available at [https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf](https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf).

-->

**Désinstallation du serveur de diffusion Primetime**

Pour désinstaller le serveur de diffusion en continu, arrêtez le serveur de diffusion en continu et supprimez le répertoire pss du serveur de diffusion en continu dans le répertoire Primetime .

## Utilisation de Live Packager et du serveur d’origine 1.4 {#working-with-live-packager-and-origin-server}

Cette section s’applique lorsque Primetime Streaming Server n’est pas utilisé et que Primetime Live packager ET/OU Primetime Origin Server est déployé.

### Configuration minimale requise {#minimum-system-requirements-1}

**Configuration requise**

* La multidiffusion réseau doit être activée pour envoyer la diffusion MPEG-TS d’un encodeur vers Live Packager. Live Packager accepte également un flux RTMP provenant d’un encodeur qui ne nécessite pas de réseau à diffusion multiple.

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon double ® ou plus rapide recommandé)
* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandé)
* Carte Ethernet 1 Go recommandée (plusieurs cartes réseau et 10 Go également pris en charge)
* Disque :

   * (Disk-SAS) : 10 Go minimum avec 7,5 K tr/min
   * (Disque-SSD) : 400 Mbit/s en lecture/écriture
   * (NAS) : lien dédié 1 Go

**Exigences logicielles**

* Oracle Java JRE 1.7 (Recommandé : JVM Sun/Oracle Hotspot). Le JDK est requis pour l’accès de JConsole aux API JMX.

La configuration minimale requise ci-dessus s’applique également au serveur d’origine et à Live Packager.

### Installation et configuration de Live Packager {#install-and-configure-the-live-packager}

**Installation de Live Packager**

1. Téléchargez le logiciel Java SE et JDK à partir du [Oracle site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) et suivez les instructions d’installation.
1. Extraire le fichier d’archive Adobe Primetime - Live Packager 1.4 `Primetime-LivePackager-1-4-0-b206-12042014.zip` sur votre disque.

**Installation du serveur d’origine HTTP**

1. Téléchargez le logiciel Java JRE et JDK à partir du [Oracle site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) et suivez les instructions d’installation.
1. Extrayez le fichier d’archive Adobe Primetime - HTTP Origin Server 1.4, `Primetime-HttpOrigin-1-4-0-b206-12042014.zip`, sur votre disque.

**Pour démarrer Live Packager** Pour démarrer le module, exécutez la commande suivante à partir du répertoire racine du module :\
`$packager_start.sh`

**Démarrage du serveur d’origine HTTP**

Pour démarrer le serveur d’origine HTTP, exécutez la commande suivante à partir de la ligne de commande du répertoire racine du serveur d’origine :\
`$./origin_start.sh`

**Arrêt de Live Packager**

Pour arrêter le module, exécutez la commande suivante à partir du répertoire racine du module :\
`$packager_stop.sh`

**Arrêtez le serveur d’origine HTTP**

Pour arrêter le serveur d’origine HTTP, exécutez la commande suivante dans le répertoire racine du serveur d’origine :\
`$./origin_stop.sh`

**Redémarrage de Live Packager**

Pour redémarrer le module, arrêtez et démarrez le module.

**Remarque**: lorsque le programme de package démarre, il tente d’initialiser les informations d’amorçage à partir de la cible du fragment dans le répertoire temporaire. Si les informations de bootstrap sont trouvées dans la cible du fragment, cela signifie que le programme de package a été redémarré. En cas de redémarrage, le module attend jusqu’à la limite de fragment suivante, puis commence le conditionnement. Le programme de package insère une entrée d’espace dans le bootstrap pour indiquer qu’il manque des fragments.

**Redémarrer le serveur d’origine HTTP**

Pour redémarrer le serveur d’origine HTTP, arrêtez et démarrez le serveur d’origine HTTP.

**Configuration de Live Packager**

Le fichier de distribution contient un exemple de configuration qui peut être utilisé pour tester le programme de package.

Après avoir extrait l’archive Adobe Primetime - Live Packager 1.4, remplacez les répertoires par le répertoire de packager, puis exécutez le script packager_start.sh. L’exemple de configuration écoute l’adresse de multidiffusion 239.235.0.3:14000 et exécute le serveur d’origine local sur le port 8080. La sortie est configurée pour être écrite dans la variable `packager/webroot/_default_/_default_/ directory`.

<!-- 

Comment Type: draft

For more details about the configuration refer [the Primetime Live Packager document](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

-->

**Configuration du serveur d’origine HTTP**

Consultez le document Prise en main du serveur d’origine HTTP Primetime pour obtenir les détails de configuration disponibles ici.

**Désinstallation de Live Packager**

Pour désinstaller le programme de package, arrêtez le programme de package et supprimez le répertoire du programme de package du répertoire Primetime.

**Désinstallation du serveur HTTP d’origine**

Pour désinstaller le serveur d’origine HTTP, arrêtez le serveur d’origine HTTP et supprimez le répertoire httporigin du serveur d’origine HTTP dans le répertoire Primetime.

## Adobe Primetime Offline Packager 1.4 {#adobe-primetime-offline-packager}

### Configuration minimale requise {#minimum-system-requirements-2}

**Systèmes d’exploitation pris en charge**

* Linux CentOS 6.3 64 bits

**Configuration matérielle requise**

* Processeur Intel® Pentium® 4 3,2 GHz (Intel Xeon double ® ou plus rapide recommandé)
* Systèmes d’exploitation 64 bits : 4 Go de RAM (8 Go recommandé)
* Carte Ethernet 1 Go recommandée (plusieurs cartes réseau et 10 Go également pris en charge)
* Disque :

   * (Disk-SAS) : 10 Go minimum avec 7,5 K tr/min
   * (Disque-SSD) : 400 Mbit/s en lecture/écriture
   * (NAS) : lien dédié 1 Go

**Exigences logicielles**

* Oracle de Java JRE 1.7 ou version ultérieure.

### Installation et configuration du module hors ligne {#install-and-configure-offline-packager}

Pour installer Offline Packager, procédez comme suit :

1. Téléchargez le logiciel Java SE à partir du [Oracle site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) et suivez les instructions d’installation.
1. Extrayez le fichier d’archive Adobe Primetime - Offline Packager 1.4, `Primetime- OfflinePackager-1-4-0-b206-12042014.zip`, sur votre disque.

Consultez le document Prise en main de Primetime Offline Packager pour obtenir les détails de configuration disponibles. [here](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://helpx.adobe.com/support/primetime.html) page.
