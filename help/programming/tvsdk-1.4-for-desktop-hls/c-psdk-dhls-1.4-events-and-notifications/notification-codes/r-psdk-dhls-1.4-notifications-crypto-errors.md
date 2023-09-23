---
description: Le module de cryptage du moteur vidéo Adobe renvoie ces notifications dans l’objet de métadonnées NATIVE_ERROR.
title: Valeurs de chiffrement NATIVE_ERROR
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 8%

---

# NATIVE_ERROR : valeurs de chiffrement{#native-error-crypto-values}

Le module de cryptage du moteur vidéo Adobe renvoie ces notifications dans l’objet de métadonnées NATIVE_ERROR.

| Valeur de la clé de métadonnées RUNTIME_CODE | Valeur de la clé de métadonnées RUNTIME_CODE_MESSAGE | Signification |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | L’algorithme utilisé n’est pas pris en charge. |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | Les données sont corrompues. |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | Mémoire tampon trop petite. |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | Certificat incorrect. |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | Mise à jour du résumé. |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | Finit le condensé. |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | Paramètre incorrect. |
