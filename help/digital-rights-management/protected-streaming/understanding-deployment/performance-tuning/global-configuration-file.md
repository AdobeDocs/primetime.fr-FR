---
description: Cette rubrique décrit les considérations liées aux performances. Tous les paramètres du fichier de configuration globale appelés flashaccess-global.xml affectent les performances.
title: Fichier de configuration global
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Optimisation des performances {#performance-tuning}

Cette rubrique décrit les considérations liées aux performances. Tous les paramètres du fichier de configuration globale appelés flashaccess-global.xml affectent les performances.

## Fichier de configuration global {#global-configuration-file}

Le fichier de configuration comprend les éléments de paramètres suivants :

* `<Caching>` La variable `<Caching>` contrôle la mise en cache des fichiers de configuration en mémoire. La variable `<Caching>` prend en charge la syntaxe suivante :

```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
```

* `refreshDelaySeconds` Contrôle la fréquence à laquelle le serveur recherche les mises à jour des fichiers de configuration. Une valeur faible pour `refreshDelaySeconds` a un impact négatif sur les performances, tandis qu’une valeur plus élevée peut améliorer les performances.

  Voir *Mise à jour des fichiers de configuration* pour plus d’informations sur `refreshDelaySeconds`.

* `numTenants` indique le nombre de clients. Une valeur inférieure au nombre de clients affecte les performances car les requêtes envoyées aux clients restants entraînent des pertes de cache. Une absence de cache pour toutes les données de configuration affecte négativement les performances. Par conséquent, il est recommandé de définir cette valeur plus élevée que le nombre de clients configurés pour le serveur, sauf si vous devez tenir compte de limitations de mémoire.

* `<Logging>` La variable `<Logging>` spécifie le niveau de journalisation et la fréquence de roulage des fichiers journaux. La variable `<Logging>` prend en charge la syntaxe suivante :

  ```
  <Logging level="..." rollingFrequency="..."/>
  ```

* `<level>`  `level` spécifie les messages à un journal. Une valeur de `DEBUG` génère de nombreux messages de journal, ce qui peut avoir une incidence négative sur les performances. Il est recommandé d’appliquer un paramètre de `WARN` pour des performances optimales. Cependant, cette valeur peut entraîner la perte d’informations d’exécution essentielles, telles que les audits des licences. Si vous souhaitez enregistrer les informations du journal avec un impact minimal sur les performances, vous devez appliquer une valeur de `INFO`.

* `<rollingFrequency>`  `rollingFrequency` indique la fréquence à laquelle les fichiers journaux *roulé*. *`Rolling`* est un processus qui désigne tout nouveau fichier journal en tant que journal actif. Par conséquent, le fichier journal précédemment actif ne peut plus être modifié et est considéré comme *`rolled`*. Vous pouvez définir l’intervalle variable sur `MINUTELY`, `HOURLY`, `TWICE-DAILY`, `DAILY`, `WEEKLY`, `MONTHLY`, ou `NEVER`.

Voir *Utilisation du SDK Adobe Primetime DRM pour la protection du contenu* pour obtenir des conseils sur l’optimisation des performances.
