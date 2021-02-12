---
title: Transcodage et normalisation
description: null
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---


# Transcodage et normalisation {#transcoding-and-normalization}

L’Ad Insertion Primetime tente de garantir une expérience d’affichage cohérente dans le contenu et les publicités en tentant de faire correspondre :

1. Codecs de flux source et débits, tout en sélectionnant systématiquement la création de qualité/débit optimale lors du transcodage

1. Taille des fragments de flux source (HLS/#EXT-X-TARGETDURATION)

1. Formats créatifs préférés pour le transcodage

1. Auto-audit audio pour garantir un niveau dB cohérent pour toutes les créations publicitaires.

>[!NOTE]
>
>Les ressources HLS générées par le transcodage juste à temps de l’Ad Insertion Primetime produisent des ressources HLS de la version 3, quelle que soit la version HLS définie dans le contenu.