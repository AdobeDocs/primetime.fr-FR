---
seo-title: Réglage des performances
title: Réglage des performances
uuid: db8889c7-ecf5-4551-a6fc-1d3ab992b9ff
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Réglage des performances{#performance-tuning}

Suivez les conseils suivants pour améliorer les performances :

* L’utilisation d’un HSM réseau peut être beaucoup plus lente que l’utilisation d’un HSM directement connecté.
* Pour améliorer les performances, vous pouvez éventuellement activer la prise en charge native des opérations de chiffrement en déployant les bibliothèques spécifiques à la plate-forme situées dans le [!DNL thirdparty/cryptoj] dossier du SDK. Pour activer la prise en charge native, ajoutez la bibliothèque pour votre plateforme (jsafe.dll pour Windows ou libjsafe.so pour Linux) au chemin d’accès.

   >[!NOTE] {class=&quot;- rubrique/note &quot;}
   >
   >Si vous exécutez plusieurs applications Web dans la même instance Tomcat et que vous avez `jsafe.dll` sur le chemin d’accès, seule la première application Web chargée est en mesure de charger la `jsafe.dll` bibliothèque. Par conséquent, seule la première application Web bénéficie du support natif. Dans de tels cas, pour améliorer les performances de toutes les applications Web, placez `cryptoj.jar`hors du fichier WAR. Par exemple, dans le `<tomcat_installation_folder>/lib` répertoire.

* Un système d’exploitation 64 bits, tel que la version 64 bits de Red Hat® ou de Windows, offre de bien meilleures performances qu’un système d’exploitation 32 bits.

## Génération de nombres aléatoires (Linux) {#section_3E2E936A538F40B7BF8892C65E117907}

Sous certaines conditions, le Linux   peut s&#39;interrompre lors d&#39;opérations liées à la gestion des droits numériques Primetime qui nécessitent une génération aléatoire de nombres, notamment :

* Démarrage du serveur Adobe Primetime DRM License Server
* Génération de stratégies à l’aide de l’ [!DNL AdobePolicyManager] utilitaire
* Mise en package de contenu protégé par DRM avec Adobe Media Server ou Primetime OfflinePackager

Les retards au cours de ces opérations sont souvent le résultat d&#39;un pool à faible entropie sur votre serveur Linux.

Sous Linux, des nombres aléatoires sont générés à partir du serveur  du pool d&#39;entropie . Le pool d&#39;entropie est normalement maintenu en recevant les interruptions matérielles du noyau Linux. Si un serveur est isolé et ne reçoit pas d&#39;entrée régulière des ressources du matériel (souris ou clavier, par exemple), les attentes de remplissage du pool d&#39;entropie peuvent être étendues. Dans ce scénario, les opérations en attente de données [!DNL /dev/random] peuvent être suspendues.

Vous pouvez utiliser des générateurs de nombres aléatoires matériels sur les serveurs Linux pour vous assurer que l&#39;entropie est suffisante. Toutefois, si les générateurs de nombres aléatoires matériels ne sont pas disponibles dans un scénario de déploiement donné, vous pouvez utiliser des solutions logicielles pour augmenter le taux d&#39;actualisation du pool d&#39;entropie. Une de ces solutions logicielles sous Linux est [!DNL haveged] (HArdware Volatile Entropy Gathering and Expansion daemon).

## Détermination de l&#39;entropie disponible {#section_686B311FE6144566B6939E9F20915ADC}

Pour vérifier le nombre de bits disponibles dans le pool d&#39;entropie d&#39;un serveur donné pendant un délai imprévu, exécutez la commande suivante :

```
cat /proc/sys/kernel/random/entropy_avail 
```

Un système Linux sain avec beaucoup d&#39;entropie disponible retournera près des 4 096 bits d&#39;entropie complets. Si la valeur renvoyée est inférieure à 200, le système fonctionne très peu sur l’entropie.
