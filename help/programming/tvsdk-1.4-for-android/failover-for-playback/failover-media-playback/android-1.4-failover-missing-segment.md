---
description: Lorsqu’un segment est manquant, par exemple lorsqu’un téléchargement d’un segment donné échoue, tente de récupérer par le biais de plusieurs tentatives de basculement. S’il ne peut pas récupérer, une erreur est générée.
seo-description: Lorsqu’un segment est manquant, par exemple lorsqu’un téléchargement d’un segment donné échoue, tente de récupérer par le biais de plusieurs tentatives de basculement. S’il ne peut pas récupérer, une erreur est générée.
seo-title: Basculement de segment manquant
title: Basculement de segment manquant
uuid: 17ee1221-e1eb-4f64-a406-4d7eff1d7555
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Basculement de segment manquant{#missing-segment-failover}

Lorsqu’un segment est manquant, par exemple lorsqu’un téléchargement d’un segment donné échoue, tente de récupérer par le biais de plusieurs tentatives de basculement. S’il ne peut pas récupérer, une erreur est générée.

Si un segment est manquant sur le serveur, car, par exemple, le fichier manifeste n’est pas présent, le segment ne peut pas être téléchargé, etc., TVSDK tente d’échouer en essayant d’exécuter les options suivantes :

1. Tentez un basculement sur incident vers le même segment, au même débit, dans un fichier de variante.
1. Basculez vers un autre débit binaire (commutateur ABR) dans le même fichier.
1. Parcourez chaque débit disponible dans chaque variante disponible.
1. Ignorez le segment et émettez un avertissement.

Lorsque TVSDK ne peut pas obtenir un autre segment, il déclenche une notification d’erreur `CONTENT_ERROR`. Cette notification contient une notification interne avec le code `DOWNLOAD_ERROR`. Si le flux présentant le problème est une autre piste audio, génère la notification d&#39;erreur `AUDIO_TRACK_ERROR`.

Si le moteur vidéo ne parvient pas à obtenir des segments en permanence, il limite les sauts de segment continus à 5, après quoi la lecture est arrêtée et émet un `NATIVE_ERROR` avec le code 5.

>[!NOTE]
>
>Les paramètres de contrôle de débit binaire adaptatif (ABR) ne sont pas pris en compte lorsqu’un basculement survient. En effet, le mécanisme de basculement est conçu pour utiliser n’importe laquelle des listes de lecture actuellement disponibles, quel que soit leur profil de débit, comme flux de sauvegarde.
>
>Lors d&#39;une opération de basculement, il peut y avoir un commutateur de profil. Si une erreur se produit lors du téléchargement d’un des segments de la liste de lecture, les paramètres de contrôle ABR tels que le débit minimal/maximal autorisé sont ignorés.

