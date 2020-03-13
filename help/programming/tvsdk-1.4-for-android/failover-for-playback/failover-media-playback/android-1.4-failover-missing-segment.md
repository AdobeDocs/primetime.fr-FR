---
description: Lorsqu’un segment est manquant, par exemple lorsqu’un téléchargement d’un segment donné échoue, tente de récupérer par le biais de diverses tentatives de basculement. S’il ne parvient pas à récupérer, une erreur est générée.
seo-description: Lorsqu’un segment est manquant, par exemple lorsqu’un téléchargement d’un segment donné échoue, tente de récupérer par le biais de diverses tentatives de basculement. S’il ne parvient pas à récupérer, une erreur est générée.
seo-title: Basculement de segment manquant
title: Basculement de segment manquant
uuid: 17ee1221-e1eb-4f64-a406-4d7eff1d7555
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Basculement de segment manquant{#missing-segment-failover}

Lorsqu’un segment est manquant, par exemple lorsqu’un téléchargement d’un segment donné échoue, tente de récupérer par le biais de diverses tentatives de basculement. S’il ne parvient pas à récupérer, une erreur est générée.

Si un segment est manquant sur le serveur, car, par exemple, le fichier manifeste n’est pas présent, le segment ne peut pas être téléchargé, et ainsi de suite, TVSDK tente d’échouer en essayant les options suivantes :

1. Tentez un basculement vers le même segment, au même débit, dans un fichier de variante.
1. Passez à un autre débit (commutateur ABR) dans le même fichier.
1. Parcourez tous les débits disponibles dans chaque variante disponible.
1. Ignorez le segment et émettez un avertissement.

Lorsque TVSDK ne parvient pas à obtenir un autre segment, il déclenche une notification d’ `CONTENT_ERROR` erreur. Cette notification contient une notification interne avec le `DOWNLOAD_ERROR` code de code. Si le flux comportant le problème est une autre piste audio, génère la notification `AUDIO_TRACK_ERROR` d’erreur.

Si le moteur vidéo ne parvient pas à obtenir en continu les segments, il limite les sauts de segments continus à 5, après quoi la lecture est arrêtée et émet une erreur `NATIVE_ERROR` avec le code 5.

>[!NOTE]
>
>Les paramètres de contrôle de débit binaire adaptatif (ABR) ne sont pas pris en compte lorsqu’un basculement survient. En effet, le mécanisme de basculement est conçu pour utiliser n’importe laquelle des listes de lecture actuellement disponibles, quel que soit leur  de débit binaire, comme flux de sauvegarde.
>
>Lors d’une opération de basculement, il peut y avoir un commutateur . Si une erreur se produit lors du téléchargement d’un des segments de la liste de lecture, les paramètres de contrôle ABR tels que le débit minimal/maximal autorisé sont ignorés.

