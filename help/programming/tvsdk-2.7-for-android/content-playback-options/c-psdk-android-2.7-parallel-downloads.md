---
description: Le téléchargement de fichiers vidéo et audio en parallèle, plutôt que dans une série, réduit les délais de démarrage.
seo-description: Le téléchargement de fichiers vidéo et audio en parallèle, plutôt que dans une série, réduit les délais de démarrage.
seo-title: Téléchargements parallèles
title: Téléchargements parallèles
uuid: fa3edb50-7c24-433c-bc50-72d6cf73d834
translation-type: tm+mt
source-git-commit: 51b3713e04fcb4adeaa7a8d1b700372b1dba7cf6
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# Téléchargements parallèles {#parallel-downloads}

Le téléchargement de fichiers vidéo et audio en parallèle, plutôt que dans une série, réduit les délais de démarrage.

Les téléchargements parallèles permettent de lire des fichiers vidéo à la demande (VOD), d’optimiser l’utilisation de la bande passante disponible à partir d’un serveur, de réduire la probabilité de se retrouver dans des situations de mémoire tampon en cours d’exécution et de réduire le délai entre le téléchargement et la lecture.

<!-- 

Removed as part of "no DASH use cases" for 2.5.1, May 31st, 2017 release.
<p>Parallel downloads allows DASH video-on-demand (VOD) files to be played, optimizes the available bandwidth usage from a server, lowers the probability of getting into buffer under-run situations, and minimizes the delay between download and playback. </p>

 -->

Sans téléchargements parallèles, TVSDK émet une requête pour le segment vidéo et, une fois le segment vidéo chargé, il demande un ou deux segments audio. Avec les téléchargements parallèles, les segments audio et vidéo sont téléchargés simultanément, et non de manière séquentielle. En outre, comme il existe deux connexions et deux requêtes HTTP par segment en parallèle, les données atteignent l’écran plus rapidement.

>[!NOTE]
>
>Cette fonctionnalité s’applique uniquement au contenu dans lequel l’audio et la vidéo sont codés dans différents fichiers (contenu non muxé) et ne s’applique pas au contenu MP4, qui est toujours muxed. Le contenu HLS est souvent non muxé, en particulier avec des fichiers audio alternatifs.

<!-- 

See comment above (DASH use case removed).
  This feature applies only to content where the audio and video are encoded into different files (unmuxed content) and does not apply to MP4 content, which is always muxed. Most DASH content is unmuxed, and HLS content is often unmuxed, especially with alternate audio. 
-->

La connexion HTTP peut connaître des retards aux étapes suivantes :

* Lors de l’établissement de la connexion TCP/IP au serveur

   Bien que le client et le serveur aient accepté de communiquer, aucune communication HTTP n&#39;a encore été effectuée. Ce type de délai dépend de l’infrastructure entre le client et le serveur. Ce processus nécessite de trouver un chemin d&#39;accès via Internet entre le client et le serveur et de s&#39;assurer que tous les périphériques, tels que les routeurs et les pare-feu, sur l&#39;itinéraire acceptent le transfert de données.
* Lors de l’envoi d’une demande HTTP pour un segment ou un manifeste sur la connexion TCP/IP.

   Le serveur reçoit la demande, la traite et les débuts lui retransmettent les données. Le degré de retard dépend de la charge et de la complexité du logiciel sur le serveur et, dans une certaine mesure, de la vitesse de connexion de transfert lorsque le client envoie la demande.

