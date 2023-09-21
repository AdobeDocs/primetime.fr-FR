---
title: Durée de mise en cache de la licence
description: Durée de mise en cache de la licence
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Durée de mise en cache de la licence{#license-caching-duration}

La durée de mise en cache des licences indique la durée pendant laquelle une licence peut être mise en cache sur le disque dans le magasin de licences local du client sans nécessiter de nouvelle acquisition de la part du serveur de licences. Vous pouvez également spécifier une date et une heure absolues au-delà desquelles une licence ne peut plus être mise en cache.

Une fois la date d’expiration du cache passée, la licence n’est plus valide et le client doit demander une nouvelle licence au serveur de licences.

Exemple de cas d’utilisation : utilisez la durée de mise en cache d’une licence pour spécifier une durée de validité fixe pour une licence spécifique, comme dans un cas d’utilisation de location. Vous pouvez indiquer une location de 30 jours (avec mise en cache de licence) pour indiquer la durée totale de la licence pendant laquelle le contenu doit être consommé.
