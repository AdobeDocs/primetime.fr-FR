---
title: Transcodage et normalisation
description: Transcodage et normalisation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Transcodage et normalisation {#transcoding-and-normalization}

L’Ad Insertion Primetime tente d’assurer une expérience de visionnage cohérente pour l’ensemble du contenu et des publicités en tentant de créer des correspondances :

1. Codecs de flux source et débits, tout en sélectionnant toujours le créatif de qualité/débit le plus élevé lors du transcodage

1. Taille des fragments de flux source (HLS/#EXT-X-TARGETDURATION)

1. Formats créatifs préférés pour le transcodage

1. Automatisation de l’audio pour garantir un niveau dB cohérent pour tous les créatifs publicitaires.

>[!NOTE]
>
>Les ressources HLS générées par le transcodage juste à temps de l’Ad Insertion Primetime produisent des ressources HLS de la version 3, quelle que soit la version HLS définie dans le contenu.
