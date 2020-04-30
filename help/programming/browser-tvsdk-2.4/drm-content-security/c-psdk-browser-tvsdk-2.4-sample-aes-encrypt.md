---
description: Bien que la méthode de chiffrement AES-128 chiffre l’ensemble du conteneur de flux de transport (TS), y compris les en-têtes, le chiffrement SAMPLE-AES ne chiffre que l’audio et une partie des données vidéo.
seo-description: Bien que la méthode de chiffrement AES-128 chiffre l’ensemble du conteneur de flux de transport (TS), y compris les en-têtes, le chiffrement SAMPLE-AES ne chiffre que l’audio et une partie des données vidéo.
seo-title: Exemples de flux HLS chiffrés AES
title: Exemples de flux HLS chiffrés AES
uuid: 32c1f87b-eb81-4e1c-92ea-ec37260a7ecb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Exemples de flux HLS chiffrés AES{#sample-aes-encrypted-hls-streams}

Bien que la méthode de chiffrement AES-128 chiffre l’ensemble du conteneur de flux de transport (TS), y compris les en-têtes, le chiffrement SAMPLE-AES ne chiffre que l’audio et une partie des données vidéo.

Dans les flux chiffrés, un bloc protégé est identifié sur lequel le processus de protection est terminé. Les blocs vidéo protégés H.264 sont le corps des types 1 et 5 des unités de couche d&#39;adaptation réseau (NAL). Un bloc audio protégé est une image audio, et l’audio doit être au format AAC.

>[!IMPORTANT]
>
>Vous devez avoir la clé et le vecteur d’initialisation (IV). Le navigateur TVSDK utilise la clé et IV pour déchiffrer le flux avant de le lire.

Chaque bloc protégé contient un entier de blocs de 16 octets chiffrés en utilisant le mode de chaînage par blocs de chiffrement AES-128 (CBC) sans remplissage. Radio-Canada se trouve dans chaque bloc protégé et, en début de chaque nouveau bloc protégé, le IV doit être remis à sa valeur d&#39;origine.

Les codecs suivants sont pris en charge :

* Pour la vidéo, H.264 est pris en charge.
* Pour les fichiers audio, sample-AES est pris en charge uniquement pour AAC.

