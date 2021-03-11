---
title: Réglage des performances
description: Réglage des performances
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# Réglage des performances{#performance-tuning}

Suivez les conseils suivants pour améliorer les performances :

* L’utilisation d’un HSM réseau peut être beaucoup plus lente que l’utilisation d’un HSM directement connecté.
* Pour améliorer les performances, vous pouvez éventuellement activer la prise en charge native des opérations de cryptographie en déployant les bibliothèques spécifiques à la plate-forme situées dans le dossier [!DNL thirdparty/cryptoj] du SDK. Pour activer la prise en charge native, ajoutez la bibliothèque de votre plate-forme (jsafe.dll pour Windows ou libjsafe.so pour Linux) au chemin d’accès.

   >[!NOTE]
   >
   >Si vous exécutez plusieurs applications Web dans la même instance Tomcat et que `jsafe.dll` se trouve sur le chemin d’accès, seule la première application Web chargée peut charger la bibliothèque `jsafe.dll`. Par conséquent, seule la première application Web bénéficie du support natif. Dans de tels cas, pour améliorer les performances de toutes les applications Web, placez `cryptoj.jar`en dehors du fichier WAR. Par exemple, dans le répertoire `<tomcat_installation_folder>/lib`.

* Un système d&#39;exploitation 64 bits, tel que la version 64 bits de Red Hat® ou de Windows, offre de bien meilleures performances par rapport à un système d&#39;exploitation 32 bits.

## Génération de nombres aléatoires (Linux) {#section_3E2E936A538F40B7BF8892C65E117907}

Dans certaines conditions, les environnements Linux peuvent interrompre leurs opérations liées à la gestion des droits numériques Primetime qui nécessitent la génération de nombres aléatoires, notamment :

* Démarrage du serveur de licence DRM Adobe Primetime
* Génération de stratégie à l&#39;aide de l&#39;utilitaire [!DNL AdobePolicyManager]
* Mise en package de contenu protégé par DRM avec Adobes Medium Server ou Primetime OfflinePackager

Les retards au cours de ces opérations sont souvent le résultat d&#39;un pool à faible entropie sur votre serveur Linux.

Sous Linux, des nombres aléatoires sont générés à partir du pool d’entrées de l’environnement serveur. Le pool d&#39;entropie est normalement maintenu en recevant des interruptions matérielles par le noyau Linux. Si un serveur est isolé et ne reçoit pas d&#39;entrée régulière de ressources matérielles (comme une souris ou un clavier), les attentes de remplissage du pool d&#39;entropie peuvent être étendues. Dans ce scénario, les opérations en attente de données de [!DNL /dev/random] peuvent être suspendues.

Vous pouvez utiliser des générateurs de nombres aléatoires matériels sur les serveurs Linux pour vous assurer qu&#39;une entropie suffisante est générée. Cependant, si des générateurs de nombres aléatoires matériels ne sont pas disponibles dans un scénario de déploiement donné, vous pouvez utiliser des solutions logicielles pour augmenter le taux de rafraîchissement du pool d&#39;entropie. L&#39;une de ces solutions logicielles sous Linux est [!DNL haveged] (démon HArdware Volatile Entropy Gathering and Expansion).

## Détermination de l&#39;entropie disponible {#section_686B311FE6144566B6939E9F20915ADC}

Pour vérifier le nombre de bits disponibles dans le pool d&#39;entropie d&#39;un serveur donné en cas de retard inattendu, exécutez la commande suivante :

```
cat /proc/sys/kernel/random/entropy_avail 
```

Un système Linux sain avec beaucoup d&#39;entropie disponible retournera près des 4 096 bits d&#39;entropie complets. Si la valeur retournée est inférieure à 200, le système fonctionne très peu sur l&#39;entropie.
