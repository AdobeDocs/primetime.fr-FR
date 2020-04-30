---
description: Cette rubrique décrit les considérations liées aux performances. Tous les paramètres du fichier de configuration globale appelés flashaccess-global.xml affectent les performances.
seo-description: Cette rubrique décrit les considérations liées aux performances. Tous les paramètres du fichier de configuration globale appelés flashaccess-global.xml affectent les performances.
seo-title: Fichier de configuration global
title: Fichier de configuration global
uuid: 254925b5-d441-4a35-ad6f-f99db5de7591
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Réglage des performances {#performance-tuning}

Cette rubrique décrit les considérations liées aux performances. Tous les paramètres du fichier de configuration globale appelés flashaccess-global.xml affectent les performances.

## Fichier de configuration global {#global-configuration-file}

Le fichier de configuration comprend les éléments de paramètres suivants :

* `<Caching>` L’ `<Caching>` élément contrôle la mise en cache des fichiers de configuration en mémoire. L’ `<Caching>` élément prend en charge la syntaxe suivante :

```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
```

* `refreshDelaySeconds` Contrôle la fréquence à laquelle le serveur recherche les mises à jour des fichiers de configuration. Une valeur faible pour `refreshDelaySeconds` affecte négativement les performances tandis qu’une valeur élevée peut améliorer les performances.

   Voir *Mise à jour des fichiers* de configuration pour plus d’informations sur `refreshDelaySeconds`.

* `numTenants` indique le nombre de locataires. Une valeur inférieure au nombre de locataires affecte les performances car les demandes aux locataires restants provoquent des échecs de cache. Une absence de cache pour toutes les données de configuration affecte négativement les performances. Par conséquent, il est recommandé de définir cette valeur plus élevée que le nombre de locataires configurés pour le serveur, sauf si vous devez tenir compte de limitations de mémoire.

* `<Logging>` L’ `<Logging>` élément spécifie le niveau de journalisation et la fréquence d’enregistrement des fichiers journaux. L’ `<Logging>` élément prend en charge la syntaxe suivante :

   ```
   <Logging level="..." rollingFrequency="..."/>
   ```

* `<level>`  `level` spécifie les messages à un journal. Une valeur de `DEBUG` produit de nombreux messages journaux, ce qui peut avoir une incidence négative sur les performances. Il est recommandé d’appliquer un paramètre de `WARN` pour des performances optimales. Toutefois, cette valeur peut entraîner la perte d’informations d’exécution essentielles, telles que les audits de licence. Si vous souhaitez enregistrer les informations du journal avec un impact minimal sur les performances, vous devez appliquer une valeur de `INFO`.

* `<rollingFrequency>`  `rollingFrequency` indique la fréquence à laquelle les fichiers journaux sont *roulés*. *`Rolling`* est un processus qui désigne tout nouveau fichier journal en tant que journal actif. Par conséquent, le fichier journal précédemment actif ne peut plus être modifié et est considéré comme *`rolled`*. Vous pouvez définir l’intervalle de roulement sur `MINUTELY`, `HOURLY`, `TWICE-DAILY`, `DAILY`, `WEEKLY`, `MONTHLY`ou `NEVER`.

Voir *Utilisation du SDK DRM d’Adobe Primetime pour la protection du contenu* pour obtenir des conseils sur la manière d’optimiser les performances.