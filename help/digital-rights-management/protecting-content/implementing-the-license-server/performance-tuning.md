---
title: Optimisation des performances
description: Optimisation des performances
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Optimisation des performances{#performance-tuning}

Suivez les conseils ci-dessous pour améliorer les performances :

* L’utilisation d’un HSM réseau peut être beaucoup plus lente que l’utilisation d’un HSM directement connecté.
* Pour améliorer les performances, vous pouvez éventuellement activer la prise en charge native des opérations de cryptographie en déployant les bibliothèques spécifiques à la plateforme situées dans le [!DNL thirdparty/cryptoj] du SDK. Pour activer la prise en charge native, ajoutez la bibliothèque pour votre plateforme (jsafe.dll pour Windows ou libjsafe.so pour Linux) au chemin d’accès.

  >[!NOTE]
  >
  >Si vous exécutez plusieurs applications web dans la même instance Tomcat et que vous disposez de `jsafe.dll` sur le chemin d’accès, seule la première application web chargée peut charger la variable `jsafe.dll` bibliothèque . Par conséquent, seule la première application web bénéficie de la prise en charge native. Dans ce cas, pour améliorer les performances de toutes les applications web, placez `cryptoj.jar`en dehors du fichier WAR. Par exemple, dans la variable `<tomcat_installation_folder>/lib` répertoire .

* Un système d’exploitation 64 bits, tel que la version 64 bits de Red Hat® ou Windows, offre de meilleures performances par rapport à un système d’exploitation 32 bits.

## Génération de nombres aléatoires (Linux) {#section_3E2E936A538F40B7BF8892C65E117907}

Dans certaines conditions, les environnements Linux peuvent se mettre en pause lors d’opérations liées à Primetime DRM qui nécessitent une génération aléatoire de nombres, notamment :

* Démarrage du serveur de licences Adobe Primetime DRM
* Génération de stratégies à l’aide de [!DNL AdobePolicyManager] utility
* Modules de contenu protégé par DRM avec Adobe Media Server ou Primetime OfflinePackager

Les retards pendant ces opérations sont souvent le résultat d&#39;un pool à faible entropie sur votre serveur Linux.

Sous Linux, des nombres aléatoires sont générés à partir du pool d’entropie de l’environnement serveur. Le pool d’entropie est normalement géré en recevant les interruptions matérielles par le noyau Linux. Si un serveur est isolé et ne reçoit pas d’entrée régulière des ressources du matériel (telles qu’une souris ou un clavier), les attentes de rechargement du pool d’entropie peuvent être étendues. Dans ce scénario, les opérations en attente des données de [!DNL /dev/random] peut s’interrompre.

Vous pouvez utiliser des générateurs de nombres aléatoires matériels sur les serveurs Linux pour vous assurer qu’une entropie suffisante est générée. Cependant, si aucun générateur de nombres aléatoires n’est disponible dans un scénario de déploiement donné, vous pouvez utiliser des solutions logicielles pour augmenter le taux d’actualisation du pool d’entropie. Une de ces solutions logicielle sous Linux est [!DNL haveged] (Démon de collecte et d’extension de l’entropie du programme HArdware).

## Détermination de l’entrée disponible {#section_686B311FE6144566B6939E9F20915ADC}

Pour vérifier le nombre de bits disponibles dans le pool d’entropie d’un serveur donné lors d’un délai inattendu, exécutez la commande suivante :

```
cat /proc/sys/kernel/random/entropy_avail 
```

Un système Linux sain avec beaucoup d&#39;entropie disponible retournera près des 4096 bits d&#39;entropie complets. Si la valeur renvoyée est inférieure à 200, le système est très faible en termes d’entropie.
