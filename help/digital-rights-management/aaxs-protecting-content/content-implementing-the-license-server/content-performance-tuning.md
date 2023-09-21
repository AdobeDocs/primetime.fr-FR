---
title: Optimisation des performances
description: Optimisation des performances
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Optimisation des performances{#performance-tuning}

Suivez les conseils ci-dessous pour améliorer les performances :

* L’utilisation d’un HSM réseau peut être beaucoup plus lente que l’utilisation d’un HSM directement connecté.
* Pour améliorer les performances, vous pouvez éventuellement activer la prise en charge native des opérations cryptographiques en déployant les bibliothèques spécifiques à la plateforme situées dans le dossier &quot;thirdparty/cryptoj&quot; du SDK. Pour activer la prise en charge native, ajoutez la bibliothèque pour votre plateforme (jsafe.dll pour Windows ou libjsafe.so pour Linux) au chemin d’accès.

  >[!NOTE]
  >
  >Si vous exécutez plusieurs applications web dans la même instance Tomcat et que vous disposez de `jsafe.dll` sur le chemin d’accès, seule la première application web chargée peut charger la variable `jsafe.dll` bibliothèque . Par conséquent, seule la première application web bénéficie de la prise en charge native. Dans ce cas, pour améliorer les performances de toutes les applications web, placez `cryptoj.jar`en dehors du fichier WAR. Par exemple, dans la variable `<tomcat_installation_folder>/lib` répertoire .

* Un système d’exploitation 64 bits, tel que la version 64 bits de Red Hat® ou Windows, offre de meilleures performances par rapport à un système d’exploitation 32 bits.
