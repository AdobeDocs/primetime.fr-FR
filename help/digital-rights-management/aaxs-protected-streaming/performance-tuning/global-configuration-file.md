---
seo-title: Fichier de configuration global
title: Fichier de configuration global
uuid: 48c45f56-55c2-4526-b854-5552caf21541
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Fichier de configuration global{#global-configuration-file}

L’impact le plus important sur les performances est d’utiliser les paramètres du fichier de configuration global, flashaccess-global.xml. Ces paramètres comprennent les éléments `<Caching>` et `<Logging>` .

* `<Caching>` L’ `<Caching>` élément contrôle la mise en cache des fichiers de configuration en mémoire. L’ `<Caching>` élément a la syntaxe suivante :

   ```
   <Caching refreshDelaySeconds="..." numTenants="..."/>
   ```

   * `refreshDelaySeconds` contrôle la fréquence à laquelle le serveur recherche les mises à jour des fichiers de configuration. Une valeur faible `refreshDelaySeconds` a un impact négatif sur les performances, tandis qu’une valeur élevée peut améliorer les performances. Pour plus d’informations sur `refreshDelaySeconds`la mise à jour des fichiers[de configuration, voir &quot;](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)Mise à jour des fichiers de configuration&quot;.

   * `numTenants` indique le nombre de locataires. Une valeur inférieure au nombre de locataires a probablement un impact sur les performances, car les demandes aux locataires restants entraînent des pertes de cache. Une absence de cache pour les données de configuration a un impact négatif sur les performances. Par conséquent, Adobe recommande de définir cette valeur plus élevée que le nombre de locataires configurés pour le serveur, sauf si la mémoire est insuffisante.

* `<Logging>` L’ `<Logging>` élément spécifie le niveau de journalisation et la fréquence d’enroulement des fichiers journaux. L’ `<Logging>` élément a la syntaxe suivante :

   ```
   <Logging level="..." rollingFrequency=""/>
   ```

   * `level` spécifie les messages à enregistrer. La valeur &quot;DEBUG&quot; génère beaucoup de messages de journal et peut avoir un impact négatif sur les performances. Adobe recommande d’utiliser le paramètre &quot;WARN&quot; pour des performances optimales. Toutefois, cette valeur risque de perdre les informations d’exécution essentielles, telles que les audits de licence. Pour conserver les informations précieuses du journal avec un impact minimal sur les performances, utilisez la valeur &quot;INFO&quot;.
   * `rollingFrequency` indique la fréquence à laquelle les fichiers journaux sont *roulés*. Le roulement est le processus au cours duquel un nouveau fichier journal devient le journal actif, alors que le fichier journal précédemment actif n’est plus écrit et est considéré comme enroulé. L’intervalle de roulement peut être défini sur &quot;MINUTELY&quot;, &quot;HOURLY&quot;, &quot;DOUBLE-JOUR&quot;, &quot;DAILY&quot;, &quot;HEEKLY&quot;, &quot;MENTHLY&quot; ou &quot;JAMAIS&quot;.

Voir *Utilisation du SDK Adobe Access pour la protection du contenu* pour obtenir des conseils supplémentaires sur l’optimisation des performances.
