---
title: Fichier de configuration global
description: Fichier de configuration global
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Fichier de configuration global{#global-configuration-file}

L’impact le plus important sur les performances est d’utiliser les paramètres du fichier de configuration global, flashaccess-global.xml. Ces paramètres incluent la variable `<Caching>` et `<Logging>` éléments .

* `<Caching>` La variable `<Caching>` contrôle la mise en cache des fichiers de configuration en mémoire. La variable `<Caching>` présente la syntaxe suivante :

  ```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
  ```

   * `refreshDelaySeconds` contrôle la fréquence à laquelle le serveur recherche les mises à jour des fichiers de configuration. Une valeur faible pour `refreshDelaySeconds` a un impact négatif sur les performances, tandis qu’une valeur plus élevée peut améliorer les performances. Pour plus d’informations sur `refreshDelaySeconds`, voir &quot;[Mise à jour des fichiers de configuration](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)&quot;.

   * `numTenants` indique le nombre de clients. Une valeur inférieure au nombre de clients a une incidence probable sur les performances, car les demandes aux clients restants entraînent des pertes de cache. Une absence de cache pour les données de configuration a un impact négatif sur les performances. Par conséquent, Adobe vous recommande de définir cette valeur sur une valeur supérieure au nombre de clients configurés pour le serveur, sauf en cas de limitations de mémoire.

* `<Logging>` La variable `<Logging>` spécifie le niveau de journalisation et la fréquence de roulage des fichiers journaux. La variable `<Logging>` présente la syntaxe suivante :

  ```
  <Logging level="..." rollingFrequency=""/>
  ```

   * `level` spécifie les messages à enregistrer. Une valeur &quot;DEBUG&quot; génère de nombreux messages de journal et peut avoir une incidence négative sur les performances. Adobe recommande un paramètre &quot;WARN&quot; pour des performances optimales. Toutefois, cette valeur risque de perdre les informations d’exécution essentielles, telles que les audits des licences. Pour conserver des informations de journal importantes avec un impact minimal sur les performances, utilisez la valeur &quot;INFO&quot;.
   * `rollingFrequency` indique la fréquence à laquelle les fichiers journaux *roulé*. Le roulement est le processus par lequel un nouveau fichier journal devient le journal actif, tandis que le fichier journal précédemment actif n’est plus écrit et est considéré comme roulé. L’intervalle de roulement peut être défini sur &quot;MINUTELY&quot;, &quot;HOURLY&quot;, &quot;TWICE-DAILY&quot;, &quot;DAILY&quot;, &quot;WEEKLY&quot;, &quot;MENTHLY&quot; ou &quot;NEVER&quot;.

Voir *Utilisation du SDK Adobe Access pour la protection du contenu* pour obtenir des conseils supplémentaires sur l’optimisation des performances.
