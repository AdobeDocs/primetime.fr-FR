---
description: Le téléchargement vidéo et audio en parallèle, plutôt que dans une série, réduit les délais de démarrage.
title: Téléchargements parallèles
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Téléchargements parallèles {#parallel-downloads}

Le téléchargement vidéo et audio en parallèle, plutôt que dans une série, réduit les délais de démarrage.

Les téléchargements parallèles permettent de lire des fichiers VOD (video on Demand), optimisent l’utilisation de la bande passante disponible sur un serveur, réduisent la probabilité de se mettre dans des situations de mémoire tampon en cours d’exécution et réduisent le délai entre le téléchargement et la lecture.

<!-- 

Removed as part of "no DASH use cases" for 2.5.1, May 31st, 2017 release.
<p>Parallel downloads allows DASH video-on-demand (VOD) files to be played, optimizes the available bandwidth usage from a server, lowers the probability of getting into buffer under-run situations, and minimizes the delay between download and playback. </p>

 -->

Sans téléchargements parallèles, TVSDK émet une requête pour le segment vidéo et, une fois le segment vidéo chargé, il demande un ou deux segments audio. Avec les téléchargements parallèles, les segments audio et vidéo sont téléchargés simultanément, et non de manière séquentielle. En outre, comme il existe deux connexions et deux requêtes HTTP par segment en parallèle, les données atteignent l’écran plus rapidement.

>[!NOTE]
>
>Cette fonctionnalité s’applique uniquement au contenu dont le contenu audio et vidéo est codé dans différents fichiers (contenu non muxé) et ne s’applique pas au contenu MP4, qui est toujours muxé. Le contenu HLS est souvent non muxé, en particulier avec du contenu audio alternatif.

<!-- 

See comment above (DASH use case removed).
  This feature applies only to content where the audio and video are encoded into different files (unmuxed content) and does not apply to MP4 content, which is always muxed. Most DASH content is unmuxed, and HLS content is often unmuxed, especially with alternate audio. 
-->

La connexion HTTP peut entraîner des retards aux étapes suivantes :

* Lors de l’établissement de la connexion TCP/IP au serveur

  Bien que le client et le serveur aient accepté de communiquer, aucune communication HTTP n’a encore été effectuée. Ce type de délai dépend de l’infrastructure entre le client et le serveur. Ce processus nécessite de trouver un chemin d’accès Internet entre le client et le serveur et de s’assurer que tous les appareils, tels que les routeurs et les pare-feu, sur l’itinéraire acceptent le transfert de données.
* Lors de l’envoi d’une requête HTTP pour un segment ou un manifeste via la connexion TCP/IP.

  Le serveur reçoit la demande, la traite et commence à renvoyer les données au client. Le degré de délai dépend de la charge et de la complexité du logiciel sur le serveur, ainsi que de la vitesse de connexion de chargement lorsque le client envoie la demande.
