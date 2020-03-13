---
description: TVSDK offre une expérience de type TV de pouvoir rejoindre au milieu d'une publicité, dans des flux en direct.
seo-description: TVSDK offre une expérience de type TV de pouvoir rejoindre au milieu d'une publicité, dans des flux en direct.
seo-title: Insertion partielle de coupure publicitaire
title: Insertion partielle de coupure publicitaire
uuid: b6ee62da-c4d1-42f2-b03d-f73247f8e585
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Insertion partielle de coupure publicitaire{#partial-ad-break-insertion}

TVSDK offre une expérience de type TV de pouvoir rejoindre au milieu d&#39;une publicité, dans des flux en direct.

La fonction d’insertion de coupure publicitaire partielle vous permet de simuler une expérience de type TV dans laquelle, si le client  un flux en direct dans un flux intermédiaire, il  la lecture dans ce flux intermédiaire. C&#39;est similaire à passer à un de télévision et les publicités s&#39;exécutent sans problème.

Par exemple, si un utilisateur se joint au milieu d’une coupure publicitaire de 90 secondes (trois publicités de 30 secondes), de 10 secondes dans la seconde publicité (c’est-à-dire à 40 secondes de la coupure publicitaire), la seconde publicité est lue pendant la durée restante (20 secondes), suivie de la troisième publicité.

## Suivi des publicités {#section_03AFAEAA8DA44399952DC51C5E12951E}

Les suivis publicitaires pour la publicité partiellement lue (la deuxième publicité) ne sont pas déclenchés. Dans l’exemple ci-dessus, seul le suivi de la troisième publicité est déclenché.

## Comportement avec pré-lecture {#section_7DFBFB12E63343D1A0C614F0CF9F1714}

La fonction fonctionne lorsqu’une publicité preroll est lue avec du contenu en direct. Le flux est lu à partir du point de production après la fin de la publicité preroll.

Le de coupures publicitaires est envoyé même si cette coupure publicitaire ne contient aucune publicité complète. Une publicité est considérée comme une publicité partielle, si elle est ignorée pendant plus d’une seconde. Par exemple, si un lecteur regarde une publicité qu’il a sautée pendant 800 ms, elle est considérée comme une publicité complète.
