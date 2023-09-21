---
description: TVSDK offre une expérience de type télévision de possibilité de se joindre au milieu d’une publicité, dans des diffusions en direct.
title: Insertion de coupure publicitaire partielle
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Insertion de coupure publicitaire partielle{#partial-ad-break-insertion}

TVSDK offre une expérience de type télévision de possibilité de se joindre au milieu d’une publicité, dans des diffusions en direct.

La fonction d’insertion de coupure publicitaire partielle vous permet d’imiter une expérience de type TV où, si le client lance une diffusion en direct dans une diffusion mid-roll, elle commence à être lue dans cette diffusion mid-roll. Cela revient à passer à une chaîne de télévision et les publicités s&#39;exécutent en toute transparence.

Par exemple, si un utilisateur se joint au milieu d’une coupure publicitaire de 90 secondes (trois publicités de 30 secondes), 10 secondes après la seconde publicité (c’est-à-dire à 40 secondes de la coupure publicitaire), la seconde publicité est lue pendant la durée restante (20 secondes) suivie de la troisième publicité.

## Suivi de la publicité {#section_03AFAEAA8DA44399952DC51C5E12951E}

Les dispositifs de suivi publicitaires pour la publicité partiellement lue (la deuxième publicité) ne sont pas déclenchés. Dans l’exemple ci-dessus, seul le dispositif de suivi de la troisième publicité est déclenché.

## Comportement avec preroll {#section_7DFBFB12E63343D1A0C614F0CF9F1714}

Cette fonction fonctionne lorsqu’une publicité preroll est lue avec du contenu en direct. Le flux est lu à partir du point d’activation après la fin de la publicité preroll.

Les événements de coupure publicitaire sont envoyés même si cette coupure publicitaire ne contient aucune publicité complète. Une publicité est considérée comme une publicité partielle si elle est ignorée pendant plus d’une seconde. Par exemple, si un observateur regarde une publicité qu’il a sautée pendant 800 ms, elle est considérée comme une publicité complète.
