---
description: Lorsqu’un segment est manquant, par exemple lorsqu’un téléchargement d’un segment particulier échoue, tente de le récupérer par le biais de diverses tentatives de basculement. S’il ne peut pas récupérer, une erreur s’affiche.
title: Basculement des segments manquant
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Basculement des segments manquant{#missing-segment-failover}

Lorsqu’un segment est manquant, par exemple lorsqu’un téléchargement d’un segment particulier échoue, tente de le récupérer par le biais de diverses tentatives de basculement. S’il ne peut pas récupérer, une erreur s’affiche.

Si un segment est manquant sur le serveur, car, par exemple, le fichier de manifeste n’est pas présent, le segment ne peut pas être téléchargé, etc., TVSDK tente d’échouer en essayant les options suivantes :

1. Tenter un basculement vers le même segment, au même débit, dans un fichier de variante.
1. Basculez vers un autre débit binaire (bouton ABR) dans le même fichier.
1. Parcourez tous les débits disponibles dans chaque variante disponible.
1. Ignorez le segment et générez un avertissement.

Lorsque TVSDK ne parvient pas à obtenir un autre segment, il déclenche une `CONTENT_ERROR` notification d’erreur. Cette notification contient une notification interne avec le code `DOWNLOAD_ERROR` code. Si le flux avec le problème est une autre piste audio, génère la variable `AUDIO_TRACK_ERROR` notification d’erreur.

Si le moteur vidéo ne parvient pas à obtenir des segments en continu, il limite les sauts de segment continus à 5, après quoi la lecture est arrêtée et émet une `NATIVE_ERROR` avec le code 5.

>[!NOTE]
>
>Les paramètres de contrôle de débit adaptatif (ABR) ne sont pas pris en compte lors d’un basculement. En effet, le mécanisme de basculement est conçu pour utiliser n’importe laquelle des listes de lecture actuellement disponibles, quel que soit son profil de débit, comme flux de sauvegarde.
>
>Lors d’une opération de basculement, il peut y avoir un commutateur de profil. Si une erreur se produit lors du téléchargement de l’un des segments de la liste de lecture, les paramètres de contrôle ABR tels que le débit binaire min/max autorisé sont ignorés.
