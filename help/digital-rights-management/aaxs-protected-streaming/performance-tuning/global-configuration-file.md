---
seo-title: Fichier de configuration global
title: Fichier de configuration global
uuid: 48c45f56-55c2-4526-b854-5552caf21541
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Fichier de configuration globale{#global-configuration-file}

L’impact le plus important sur les performances est l’utilisation de paramètres dans le fichier de configuration global, flashaccess-global.xml. Ces paramètres comprennent les éléments `<Caching>` et `<Logging>`.

* `<Caching>` L’ `<Caching>` élément contrôle la mise en cache des fichiers de configuration en mémoire. L’élément `<Caching>` a la syntaxe suivante :

   ```
   <Caching refreshDelaySeconds="..." numTenants="..."/>
   ```

   * `refreshDelaySeconds` contrôle la fréquence à laquelle le serveur recherche les mises à jour des fichiers de configuration. Une valeur faible pour `refreshDelaySeconds` a un impact négatif sur les performances, tandis qu’une valeur élevée peut améliorer les performances. Pour plus d&#39;informations sur `refreshDelaySeconds`, consultez &quot;[Mise à jour des fichiers de configuration](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)&quot;.

   * `numTenants` indique le nombre de locataires. Une valeur inférieure au nombre de locataires a probablement une incidence sur le rendement, car les demandes aux locataires restants entraînent des erreurs de cache. Une absence de cache pour les données de configuration a un impact négatif sur les performances. Par conséquent, Adobe vous recommande de définir cette valeur plus élevée que le nombre de locataires configurés pour le serveur, à moins que la mémoire ne soit limitée.

* `<Logging>` L’ `<Logging>` élément spécifie le niveau de journalisation et la fréquence d’enroulement des fichiers journaux. L’élément `<Logging>` a la syntaxe suivante :

   ```
   <Logging level="..." rollingFrequency=""/>
   ```

   * `level` spécifie les messages à enregistrer. La valeur &quot;DEBUG&quot; génère beaucoup de messages de journal et peut avoir un impact négatif sur les performances. Adobe recommande un paramètre &quot;WARN&quot; pour des performances optimales. Cependant, cette valeur risque de perdre les informations d’exécution essentielles, telles que les audits de licence. Pour conserver des informations précieuses de journal avec un impact minimal sur les performances, utilisez la valeur &quot;INFO&quot;.
   * `rollingFrequency` indique la fréquence à laquelle les fichiers journaux sont  *roulés*. Le roulement est le processus par lequel un nouveau fichier journal devient le journal principal, alors que le fichier journal précédemment principal n&#39;est plus écrit et est considéré comme enroulé. L’intervalle de roulement peut être défini sur &quot;MINUTELY&quot;, &quot;HOURLY&quot;, &quot;DOUZE-DAILY&quot;, &quot;DAILY&quot;, &quot;HEEKLY&quot;, &quot;MENTHLY&quot; ou &quot;NEVER&quot;.

Voir *Utilisation du SDK d’accès aux Adobes pour la protection du contenu* pour obtenir des conseils supplémentaires sur l’optimisation des performances.
