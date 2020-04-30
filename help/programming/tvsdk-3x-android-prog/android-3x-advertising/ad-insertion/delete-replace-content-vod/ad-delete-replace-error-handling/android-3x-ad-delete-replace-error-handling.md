---
description: TVSDK traite les erreurs de plage de temps en fonction du problème spécifique en fusionnant ou en réordonnant les plages de temps mal définies.
seo-description: TVSDK traite les erreurs de plage de temps en fonction du problème spécifique en fusionnant ou en réordonnant les plages de temps mal définies.
seo-title: Gestion des erreurs de suppression et de remplacement des publicités
title: Gestion des erreurs de suppression et de remplacement des publicités
uuid: 615f42b7-733a-49c4-bd7a-f14ad0d23fa0
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# Gestion des erreurs de suppression et de remplacement des publicités  {#ad-deletion-and-replacement-error-handling}

TVSDK traite les erreurs de plage de temps en fonction du problème spécifique en fusionnant ou en réordonnant les plages de temps mal définies.

TVSDK gère `timeRanges` les erreurs par le biais de processus de fusion et de réorganisation par défaut. Tout d’abord, le lecteur trie les plages de temps définies par le client en fonction de l’heure de *début* . En fonction de cet ordre de tri, s’il existe des sous-ensembles et des intersections entre les plages, TVSDK fusionne les plages adjacentes et les joint.

TVSDK traite les erreurs de plage de temps avec les options suivantes :

* **Le TVSDK désordonné** réorganise les plages de temps.

* **Le sous-ensemble** TVSDK fusionne les sous-ensembles de plages temporelles.

* **L’intersection** de TVSDK fusionne les plages de temps qui se croisent.

* **Le conflit** Replace Range TVSDK sélectionne la durée de remplacement à partir du plus ancien conflit `timeRange` apparaissant dans le groupe en conflit.

TVSDK gère les conflits en mode de signalisation avec les métadonnées publicitaires de différentes manières :

* Si le mode de signalisation de la publicité est en conflit avec les métadonnées de la plage de temps, les métadonnées de la plage de temps ont toujours la priorité.

   Par exemple, si le mode de signalisation de la publicité est défini en tant que carte du serveur ou indices de manifeste et qu’il existe également des plages de temps MARK dans les métadonnées de la publicité, le comportement obtenu est que les plages sont marquées et qu’aucune publicité n’est insérée.
* Pour les plages REPLACE, si le mode de signalisation est défini en tant que carte du serveur ou indices de manifeste, les plages sont remplacées comme spécifié dans les plages REPLACE et il n&#39;y a pas d&#39;insertion publicitaire par le biais du mappage du serveur ou des indices de manifeste.

   Pour plus d’informations, voir le tableau Comportements *de combinaison de* signature et de métadonnées dans [Effet sur l’insertion et la suppression d’annonces en mode](../../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/delete-replace-content-vod/android-3x-signaling-mode-android.md)de signalisation.

Souvenez-vous des points suivants :

* Lorsque le serveur ne renvoie pas de valeur valide `AdBreaks`, TVSDK génère et traite un `NOPTimelineOperation` pour AdBreak vide, et aucune publicité n’est lue.

* Bien que la fonction de suppression/remplacement de publicités C3 soit destinée à être prise en charge uniquement pour VOD, si elle est spécifiée dans les métadonnées de la publicité, des plages de temps sont également traitées pour les flux en direct.
