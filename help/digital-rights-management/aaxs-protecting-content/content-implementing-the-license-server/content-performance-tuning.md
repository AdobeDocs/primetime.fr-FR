---
seo-title: Réglage des performances
title: Réglage des performances
uuid: bb5321a0-48ef-49cb-aaf0-00d7ab9562fe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Réglage des performances{#performance-tuning}

Suivez les conseils suivants pour améliorer les performances :

* L’utilisation d’un HSM réseau peut être beaucoup plus lente que l’utilisation d’un HSM directement connecté.
* Pour améliorer les performances, vous pouvez éventuellement activer la prise en charge native des opérations de cryptographie en déployant les bibliothèques spécifiques à la plate-forme situées dans le dossier &quot;thirdparty/cryptoj&quot; du SDK. Pour activer la prise en charge native, ajoutez la bibliothèque de votre plate-forme (jsafe.dll pour Windows ou libjsafe.so pour Linux) au chemin d’accès.

   >[!NOTE] {class=&quot;- rubrique/note &quot;}
   >
   >Si vous exécutez plusieurs applications Web dans la même instance Tomcat et que vous avez `jsafe.dll` le chemin d’accès, seule la première application Web chargée peut charger la `jsafe.dll` bibliothèque. Par conséquent, seule la première application Web bénéficie du support natif. Dans de tels cas, pour améliorer les performances de toutes les applications Web, placez `cryptoj.jar`hors du fichier WAR. Par exemple, dans le `<tomcat_installation_folder>/lib` répertoire.

* Un système d&#39;exploitation 64 bits, tel que la version 64 bits de Red Hat® ou de Windows, offre de bien meilleures performances par rapport à un système d&#39;exploitation 32 bits.

