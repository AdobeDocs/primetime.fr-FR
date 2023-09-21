---
description: Bien que la méthode de chiffrement AES-128 chiffre l’ensemble du conteneur de flux de transport (TS), y compris les en-têtes, le chiffrement SAMPLE-AES ne chiffre que l’audio et une partie des données vidéo.
title: Exemple de flux HLS cryptés AES
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Exemple de flux HLS cryptés AES{#sample-aes-encrypted-hls-streams}

Bien que la méthode de chiffrement AES-128 chiffre l’ensemble du conteneur de flux de transport (TS), y compris les en-têtes, le chiffrement SAMPLE-AES ne chiffre que l’audio et une partie des données vidéo.

Dans les diffusions cryptées, un bloc protégé est identifié sur lequel le processus de protection est terminé. Les blocs vidéo protégés H.264 sont le corps des types 1 et 5 des unités de couche d&#39;adaptation réseau (NAL). Un bloc de contenu audio protégé est une image audio, et l’audio doit être au format AAC.

>[!IMPORTANT]
>
>Vous devez avoir la clé et le vecteur d&#39;initialisation (IV). Le navigateur TVSDK utilise la clé et IV pour déchiffrer la diffusion avant de la lire.

Chaque bloc protégé contient un entier de blocs de 16 octets chiffrés en mode chaînage des codes postaux (CBC) avec remplissage AES-128. CBC apparaît dans chaque bloc protégé, et au début de chaque nouveau bloc protégé, l’IV doit être réinitialisé à sa valeur d’origine.

Les codecs suivants sont pris en charge :

* Pour la vidéo, H.264 est pris en charge.
* Pour le son, sample-AES est pris en charge uniquement pour AAC.
