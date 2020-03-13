---
description: TVSDK gère les erreurs de plage de temps en fonction du problème spécifique en fusionnant ou en réordonnant les plages de temps mal définies.
seo-description: TVSDK gère les erreurs de plage de temps en fonction du problème spécifique en fusionnant ou en réordonnant les plages de temps mal définies.
seo-title: Gestion des erreurs de suppression et de remplacement des publicités
title: Gestion des erreurs de suppression et de remplacement des publicités
uuid: 9a951bc4-b372-4655-8510-3f474171415d
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Présentation {#ad-deletion-and-replacement-error-handling-overview}

TVSDK gère les erreurs de plage de temps en fonction du problème spécifique en fusionnant ou en réordonnant les plages de temps mal définies.

TVSDK gère `timeRanges` les erreurs par le biais de processus de fusion et de réorganisation par défaut. Tout d’abord, le lecteur trie les plages temporelles définies par le client en fonction de l’heure de *début* . En fonction de cet ordre de tri, s’il existe des sous-ensembles et des intersections entre les plages, TVSDK fusionne les plages adjacentes et les rejoint.

TVSDK gère les erreurs de plage de temps avec les options suivantes :

* **Le kit TVSDK hors service** réorganise les plages de temps.

* **Le kit TVSDK de sous-ensemble** fusionne les sous-ensembles de la période.

* **Intersection** TVSDK fusionne les plages de temps qui se croisent.

* **Le conflit** de plages Remplacer TVSDK sélectionne la durée du remplacement à partir du plus ancien `timeRange` qui apparaît dans le groupe en conflit.

TVSDK gère les conflits en mode de signalisation avec les métadonnées publicitaires de différentes manières :

* Si le mode de signalisation de la publicité est en conflit avec les métadonnées de plage de temps, les métadonnées de plage de temps ont toujours la priorité.

   Par exemple, si le mode de signalisation de la publicité est défini comme carte du serveur ou indices de manifeste et qu’il existe également des plages de temps MARK dans les métadonnées de la publicité, le comportement résultant est que les plages sont marquées et qu’aucune publicité n’est insérée.
* Dans le cas des plages REPLACE, si le mode de signalisation est défini comme carte serveur ou comme indices manifestes, les plages sont remplacées comme spécifié dans les plages REPLACE et aucune insertion publicitaire n’est effectuée par le biais du mappage serveur ou des indices manifestes.

   Pour plus d’informations, voir le tableau Comportements *de combinaison* de signature/métadonnées dans [Effet sur l’insertion et la suppression d’une publicité depuis le mode de signalisation publicitaire...](../../../../tvsdk-2.7-for-android/ad-insertion/delete-replace-content-vod/c-psdk-android-2.7-signaling-mode-metadata-combos-android.md#c_psdk_signaling-mode-metadata-combos-android).

Tenez compte des points suivants :

* Lorsque le serveur ne renvoie pas de valeur valide `AdBreaks`, TVSDK génère et traite un `NOPTimelineOperation` pour l’AdBreak vide, et aucune publicité n’est lue.

* Bien que la suppression et le remplacement de publicités C3 soient uniquement pris en charge pour VOD, si elles sont spécifiées dans les métadonnées publicitaires, les plages de temps sont également traitées pour les flux en direct.

