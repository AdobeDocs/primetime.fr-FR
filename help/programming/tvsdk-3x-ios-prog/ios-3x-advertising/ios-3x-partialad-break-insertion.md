---
description: TVSDK offre une expérience TV de la possibilité de se joindre au milieu d’une publicité, dans des flux en direct.
title: Insertion partielle de coupures publicitaires
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# Insertion partielle de coupures publicitaires {#partial-ad-break-insertion}

TVSDK offre une expérience TV de la possibilité de se joindre au milieu d’une publicité, dans des flux en direct.

La fonction d’insertion d’une coupure publicitaire partielle vous permet d’imiter une expérience TV où, si le client début un flux en direct dans une coupure intermédiaire, il début de lire dans cette coupure intermédiaire. Il est similaire à passer à un canal de télévision et les publicités fonctionnent sans accroc.

Par exemple, si un utilisateur se joint au milieu d’une coupure publicitaire de 90 secondes (trois publicités de 30 secondes), 10 secondes après la seconde publicité (c’est-à-dire à 40 secondes de la coupure publicitaire), la seconde publicité est lue pendant la durée restante (20 secondes), suivie de la troisième publicité.

## Suivi de la publicité {#section_03AFAEAA8DA44399952DC51C5E12951E}

Les suivis publicitaires pour la publicité partiellement lue (la deuxième publicité) ne sont pas déclenchés. Dans l’exemple ci-dessus, seul le suivi de la troisième publicité est déclenché.

## Comportement avec le paramètre preroll {#section_7DFBFB12E63343D1A0C614F0CF9F1714}

La fonction fonctionne lorsqu’une publicité preroll est lue avec du contenu en direct. La lecture du flux s’effectue à partir du point de production après la fin de la publicité preroll.

Les événements de coupures publicitaires sont envoyés même si cette coupure publicitaire ne contient aucune publicité complète. Une publicité est considérée comme une publicité partielle, si elle est ignorée pendant plus d’une seconde. Par exemple, si un lecteur regarde une publicité qu’il a sautée pendant 800 ms, elle est considérée comme une publicité complète.