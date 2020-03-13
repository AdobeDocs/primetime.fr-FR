---
description: Le téléchargement de fichiers vidéo et audio en parallèle, plutôt que dans une série, réduit les délais de démarrage.
seo-description: Le téléchargement de fichiers vidéo et audio en parallèle, plutôt que dans une série, réduit les délais de démarrage.
seo-title: Téléchargements parallèles
title: Téléchargements parallèles
uuid: fa3edb50-7c24-433c-bc50-72d6cf73d834
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Téléchargements parallèles {#parallel-downloads}

Le téléchargement de fichiers vidéo et audio en parallèle, plutôt que dans une série, réduit les délais de démarrage.

Les téléchargements parallèles permettent de lire des fichiers vidéo à la demande (VOD), d’optimiser l’utilisation de la bande passante disponible à partir d’un serveur, de réduire la probabilité de se retrouver dans des situations de mémoire tampon en cours d’exécution et de réduire le délai entre le téléchargement et la lecture.

<!-- 

Removed as part of "no DASH use cases" for 2.5.1, May 31st, 2017 release.
<p>Parallel downloads allows DASH video-on-demand (VOD) files to be played, optimizes the available bandwidth usage from a server, lowers the probability of getting into buffer under-run situations, and minimizes the delay between download and playback. </p>

 -->

Sans téléchargements parallèles, TVSDK émet une requête pour le segment vidéo. Une fois le segment vidéo chargé, il demande un ou deux segments audio. Avec les téléchargements parallèles, les segments audio et vidéo sont téléchargés simultanément, et non de manière séquentielle. En outre, étant donné qu’il existe deux connexions et deux requêtes HTTP par segment en parallèle, les données atteignent l’écran plus rapidement.

>[!NOTE]
>
>Cette fonctionnalité s’applique uniquement au contenu dans lequel l’audio et la vidéo sont codés dans différents fichiers (contenu non muxé) et ne s’applique pas au contenu MP4, qui est toujours muxé. Le contenu HLS est souvent non muxé, notamment avec des fichiers audio alternatifs.

<!-- 

See comment above (DASH use case removed).
<note type="restriction">
  This feature applies only to content where the audio and video are encoded into different files (unmuxed content) and does not apply to MP4 content, which is always muxed. Most DASH content is unmuxed, and HLS content is often unmuxed, especially with alternate audio. 
</note>

 -->

La connexion HTTP peut connaître des retards aux étapes suivantes :

* Lors de l’établissement de la connexion TCP/IP au serveur

   Bien que le client et le serveur aient accepté de communiquer, aucune communication HTTP n’a encore eu lieu. Ce type de délai dépend de l’infrastructure entre le client et le serveur. Ce processus nécessite de trouver un chemin via Internet entre le client et le serveur et de s&#39;assurer que tous les périphériques, tels que les routeurs et les pare-feu, sur l&#39;itinéraire acceptent le transfert de données.
* Lors de l’envoi d’une requête HTTP pour un segment ou un manifeste sur la connexion TCP/IP.

   Le serveur reçoit la requête, la traite et  envoyer les données au client. Le degré de retard dépend de la charge et de la complexité du logiciel sur le serveur et, dans une certaine mesure, de la vitesse de connexion de transfert lorsque le client envoie la requête.

